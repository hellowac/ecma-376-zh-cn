# 20.1.10 简单类型

=== "中文"

    This is the complete list of simple types dedicated to DrawingML framework.

=== "英文"

    **Simple Types**

    This is the complete list of simple types dedicated to DrawingML framework.

## 20.1.10.1 ST_AdjAngle (可调整角度)

=== "中文"

    这个简单类型是一个可调整的角度，可以是绝对角度，也可以是对几何引导的引用。可调整角度的单位是60,000分之一度。

    这个简单类型是以下类型的联合：

    - ST_Angle 简单类型 (§20.1.10.3)。
    - ST_GeomGuideName 简单类型 (§20.1.10.28)。

    [注：这个简单类型的内容模型（ST_AdjAngle）的W3C XML模式定义位于 §A.4.1。
    注：]

=== "英文"

    **ST_AdjAngle (Adjustable Angle Methods)**

    This simple type is an adjustable angle, either an absolute angle or a reference to a geometry guide. The units for an adjustable angle are 60,000ths of a degree.

    This simple type is a union of the following types:
    
    - The ST_Angle simple type (§20.1.10.3).
    - The ST_GeomGuideName simple type (§20.1.10.28).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AdjAngle) is located in §A.4.1.
    end note]

## 20.1.10.2 ST_AdjCoordinate (可调整坐标)

=== "中文"

    这个简单类型是一个可调整坐标，可以是绝对坐标位置，也可以是对几何引导的引用。

    这个简单类型是以下类型的联合：

    - ST_Coordinate 简单类型 (§20.1.10.16)。
    - ST_GeomGuideName 简单类型 (§20.1.10.28)。

    [注：这个简单类型的内容模型（ST_AdjCoordinate）的W3C XML模式定义位于 §A.4.1。注：]

=== "英文"

    **ST_AdjCoordinate (Adjustable Coordinate Methods)**

    This simple type is an adjustable coordinate is either an absolute coordinate position or a reference to a geometry guide.

    This simple type is a union of the following types:
    
    - The ST_Coordinate simple type (§20.1.10.16).
    - The ST_GeomGuideName simple type (§20.1.10.28).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AdjCoordinate) is located in §A.4.1. end note]

## 20.1.10.3 ST_Angle (角度)

=== "中文"

    这个简单类型表示60,000分之一度的角度。正角是顺时针的（即，朝着正y轴）；负角是逆时针的（即，朝着负y轴）。

    这个简单类型的内容是对W3C XML模式int数据类型的限制。

    [注：这个简单类型的内容模型（ST_Angle）的W3C XML模式定义位于 §A.4.1。注：]

=== "英文"

    **ST_Angle (Angle)**

    This simple type represents an angle in 60,000ths of a degree. Positive angles are clockwise (i.e., towards the positive y axis); negative angles are counter-clockwise (i.e., towards the negative y axis).

    This simple type's contents are a restriction of the W3C XML Schema int datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Angle) is located in §A.4.1. end
    note]

## 20.1.10.4 ST_AnimationBuildType (动画构建方式)

=== "中文"

    这个简单类型指定了动画的构建或播放方式。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    **枚举:**

    **allAtOnce**（一次性播放动画 / Animate At Once）

    :   将所有对象一起播放动画。

    [注：这个简单类型的内容模型（ST_AnimationBuildType）的W3C XML模式定义位于 §A.4.1。注：]

=== "英文"

    **ST_AnimationBuildType (Animation Build Type)**

    This simple type specifies the ways that an animation can be built, or animated.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **Enumeration:**

    **allAtOnce (Animate At Once)**

    :    Animate all objects as one.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationBuildType) is located in §A.4.1. end note]

## 20.1.10.5 ST_AnimationChartBuildType (图表动画构建方式)

=== "中文"

    这个简单类型指定了图表动画的构建方式。也就是说，它指定了图表内部的对象应该如何进行动画。

    这个简单类型是以下类型的联合：

    - ST_AnimationBuildType 简单类型 (§20.1.10.4)。
    - ST_AnimationChartOnlyBuildType 简单类型 (§20.1.10.6)。

    [注：这个简单类型的内容模型（ST_AnimationChartBuildType）的W3C XML模式定义位于 §A.4.1。注：]

=== "英文"

    **ST_AnimationChartBuildType (Chart Animation Build Type)**

    This simple type specifies the ways that a chart animation can be built. That is, it specifies the way in which the objects within the chart should be animated.

    This simple type is a union of the following types:

    - The ST_AnimationBuildType simple type (§20.1.10.4).
    - The ST_AnimationChartOnlyBuildType simple type (§20.1.10.6).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationChartBuildType) is
    located in §A.4.1. end note]

## 20.1.10.6 ST_AnimationChartOnlyBuildType (图表动画构建选项)

=== "中文"

    这个简单类型指定了仅用于对图表进行动画的构建选项。这些选项指定了图表内部的对象应该如何进行分组和动画。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    **枚举:**

    **category (类别)**

    :   按每个类别进行动画

    **categoryEl (类别元素)**

    :   按类别内的每个元素进行动画

    **series (系列) **

    :   按每个系列进行动画

    **seriesEl (系列元素) **

    :   按系列内的每个元素进行动画

    [注：这个简单类型的内容模型（ST_AnimationChartOnlyBuildType）的W3C XML模式定义位于 §A.4.1。注：]

=== "英文"

    **ST_AnimationChartOnlyBuildType (Chart only Animation Types)**

    This simple type specifies the build options available only for animating a chart. These options specify the manner in which the objects within the chart should be grouped and animated.
        
    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration:**

    **category (Catefory)**

    :    Animate by each category

    **categoryEl (Category Element)**

    :    Animate by each element within the category

    **series (Series) **

    :    Animate by each series.

    **seriesEl (Series Element) **

    :    Animate by each element within the series

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationChartOnlyBuildType) is located in §A.4.1. end note]

## 20.1.10.7 ST_AnimationDgmBuildType (Diagram动画构建方式)

=== "中文"

    这个简单类型指定了图表动画的构建方式。也就是说，它指定了图表图形对象内部的对象应该如何进行动画。

    这个简单类型是以下类型的联合：

    - ST_AnimationBuildType 简单类型 (§20.1.10.4)。
    - ST_AnimationDgmOnlyBuildType 简单类型 (§20.1.10.8)。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationDgmBuildType) is located in §A.4.1. end note]

=== "英文"

    **ST_AnimationDgmBuildType (Diagram Animation Build Type)**

    This simple type specifies the ways that a diagram animation can be built. That is, it specifies the way in which the objects within the diagram graphical object should be animated.

    This simple type is a union of the following types:
    
    - The ST_AnimationBuildType simple type (§20.1.10.4).
    - The ST_AnimationDgmOnlyBuildType simple type (§20.1.10.8).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationDgmBuildType) is located in §A.4.1. end note]

## 20.1.10.8 ST_AnimationDgmOnlyBuildType (Diagram动画构建选项)

=== "中文"

    这个简单类型指定了仅用于对图表进行动画的构建选项。这些选项指定了图表内部的对象应该如何进行分组和动画。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    **枚举:**

    **lvlAtOnce (一次性每个层级)**

    :   逐层一次性地对图表进行动画，将整个层级作为一个对象进行动画

    **lvlOne (逐层单独进行)**

    :   按层级内的元素进行动画，逐个元素进行动画

    **one (逐个元素进行)**

    :   按元素进行动画。对于树状图，动画按照图表树内的分支进行。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationDgmOnlyBuildType) is located in §A.4.1. end note]

=== "英文"

    **ST_AnimationDgmOnlyBuildType (Diagram only Animation Types)**

    This simple type specifies the build options available only for animating a diagram. These options specify the manner in which the objects within the chart should be grouped and animated.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration:**

    **lvlAtOnce (Each Level at Once)**

    :   Animate the diagram one level at a time, animating the whole level as one object

    **lvlOne (Level One-by-One) **

    :   Animate the diagram by the elements within a level, animating them one level element at a time. 

    **one (Elements One-by-One) **

    :   Animate the diagram by elements. For a tree diagram the animation occurs by branch within the diagram tree.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_AnimationDgmOnlyBuildType) is located in §A.4.1. end note]

## 20.1.10.9 ST_BevelPresetType (预设斜角)

=== "中文"

    这个简单类型表示可以应用于3D形状的一种斜角的预设。根据为形状定义的斜角类型，斜角属性的应用方式有所不同。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    **枚举:**

    **angle (角度)**

    :   [示例：考虑将角度斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **artDeco (装饰艺术)**

    :   [示例：考虑将artDeco斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **circle (圆形)**

    :   [示例：考虑将圆形斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **convex (凸出)**

    :   [示例：考虑将凸出斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **coolSlant (酷倾斜)**

    :   [示例：考虑将coolSlant斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **cross (十字)**

    :   [示例：考虑将十字斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **divot (凹槽)**

    :   [示例：考虑将凹槽斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **hardEdge (硬边)**

    :   [示例：考虑将硬边斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **relaxedInset (轻松插入)**

    :   [示例：考虑将relaxedInset斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **riblet (浅沟槽)**

    :   [示例：考虑将riblet斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **slope (斜坡)**

    :   [示例：考虑将斜坡斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    **softRound (柔和圆角)**

    :   [示例：考虑将softRound斜角类型应用于形状的以下示例：![123](./imgs/aaa.png) 结束示例]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BevelPresetType) is located in §A.4.1. end note]

    !!! info "译注"

        图片参考原pdf文档。

=== "英文"

    **ST_BevelPresetType (Bevel Presets)**

    Represents a preset for a type of bevel which can be applied to a shape in 3D. The bevel properties are applied differently depending on the type of bevel defined for a shape.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration:**

    **angle (Angle)**

    :   [Example: Consider the following example of an angle bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **artDeco (Art Deco) **

    :   [Example: Consider the following example of an artDeco bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **circle (Circle)**

    :   [Example: Consider the following example of an circle bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **convex (Convex)**

    :   [Example: Consider the following example of an convex bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **coolSlant (Cool Slant)**

    :   [Example: Consider the following example of an coolSlant bevel type applied to a shape:: ![123](./imgs/aaa.png)  end example]

    **cross (Cross)**

    :   [Example: Consider the following example of an cross bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **divot (Divot)**

    :   [Example: Consider the following example of an divot bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **hardEdge (Hard Edge)**

    :   [Example: Consider the following example of an hardEdge bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **relaxedInset (Relaxed Inset)**

    :   [Example: Consider the following example of an relaxedInset bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **riblet (Riblet)**

    :   [Example: Consider the following example of an riblet bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **slope (Slope)**

    :   [Example: Consider the following example of an slope bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    **softRound (Soft Round)**

    :   [Example: Consider the following example of an softRound bevel type applied to a shape: ![123](./imgs/aaa.png)  end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BevelPresetType) is located in §A.4.1. end note]

## 20.1.10.10 ST_BlackWhiteMode (黑白模式)

=== "中文"

    这个简单类型指定了在指定为黑白模式时对象应该如何呈现。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    - **auto** (自动): 使用自动着色呈现对象
    - **black** (黑色): 使用仅黑色着色呈现对象
    - **blackGray** (黑色和灰色): 使用黑色和灰色着色呈现对象
    - **blackWhite** (黑白): 使用黑白着色呈现对象
    - **clr** (彩色): 使用正常颜色呈现对象
    - **gray** (灰色): 使用灰色着色呈现对象
    - **grayWhite** (灰色和白色): 使用灰色和白色着色呈现对象
    - **hidden** (隐藏): 使用隐藏颜色呈现对象
    - **invGray** (反向灰色): 使用反向灰色着色呈现对象
    - **ltGray** (浅灰色): 使用浅灰色着色呈现对象
    - **white** (白色): 使用白色着色呈现对象
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BlackWhiteMode) is located in §A.4.1. end note]

=== "英文"

    **ST_BlackWhiteMode (Black and White Mode)**

    This simple type specifies how an object should be rendered when specified to be in black and white mode.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **auto** (Automatic): Object rendered with automatic coloring
    - **black** (Black): Object rendered with black-only coloring
    - **blackGray** (Black and Gray): Object rendered with black and gray coloring
    - **blackWhite** (Black and White): Object rendered within black and white coloring
    - **clr** (Color): Object rendered with normal coloring
    - **gray** (Gray): Object rendered with gray coloring
    - **grayWhite** (Gray and White): Object rendered within gray and white coloring
    - **hidden** (Hidden): Object rendered with hidden coloring
    - **invGray** (Inverse Gray): Object rendered with inverse gray coloring
    - **ltGray** (Light Gray): Object rendered with light gray coloring
    - **white** (White): Object rendered within white coloirng
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BlackWhiteMode) is located in §A.4.1. end note]

## 20.1.10.11 ST_BlendMode (Blend Mode)

=== "中文"

    这个简单类型描述了如何将一个效果渲染在另一个效果之上。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **darken**（变暗）：Darken
    - **lighten**（变亮）：Lighten
    - **mult**（叠加）：Multiply
    - **over**（覆盖）：Overlay
    - **screen**（屏幕）：Screen
    
    [注意：这个简单类型内容模型（ST_BlendMode）的W3C XML Schema定义位于§A.4.1。末尾注释]

=== "英文"

    **ST_BlendMode (Blend Mode)**

    This simple type describes how to render effects one on top of another.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **darken** (Darken): Darken
    - **lighten** (Lighten): Lighten
    - **mult** (Multiply): Multiply
    - **over** (Overlay): Overlay
    - **screen** (Screen): Screen

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BlendMode) is located in §A.4.1. end note]

## 20.1.10.12 ST_BlipCompression (Blip Compression Type)

=== "中文"

    这个类型指定了用于特定二进制大图像或图片（blip）的压缩程度。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **email**（电子邮件压缩）：适合包含在电子邮件中的压缩尺寸
    - **hqprint**（高质量打印压缩）：适合高质量打印的压缩尺寸
    - **none**（无压缩）：未使用任何压缩
    - **print**（打印压缩）：适合打印的压缩尺寸
    - **screen**（屏幕查看压缩）：适合在屏幕上查看的压缩尺寸
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BlipCompression) is located in §A.4.1. end note]

=== "英文"

    **ST_BlipCompression (Blip Compression Type)**

    This type specifies the amount of compression that has been used for a particular binary large image or picture (blip).
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **email** (Email Compression): Compression size suitable for inclusion with email
    - **hqprint** (High Quality Printing Compression): Compression size suitable for high quality printing
    - **none** (No Compression): No compression was used
    - **print** (Printing Compression): Compression size suitable for printing
    - **screen** (Screen Viewing Compression): Compression size suitable for viewing on screen
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BlipCompression) is located in §A.4.1. end note]

## 20.1.10.13 ST_ChartBuildStep (Chart Animation Build Step)

=== "中文"

    这个简单类型指定了图表动画中的一个动画构建步骤。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    - **allPts**（所有点）：为此动画构建步骤中的图表的所有点添加动画
    - **category**（类别）：为此动画构建步骤中的图表类别添加动画
    - **gridLegend**（网格和图例）：为此动画构建步骤中的图表网格和图例添加动画
    - **ptInCategory**（类别点）：为此动画构建步骤中的图表类别中的点添加动画
    - **ptInSeries**（系列点）：为此动画构建步骤中的图表系列中的点添加动画
    - **series**（系列）：为此动画构建步骤中的图表系列添加动画
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ChartBuildStep) is located in §A.4.1. end note]

=== "英文"

    **ST_ChartBuildStep (Chart Animation Build Step)**

    This simple type specifies an animation build step within a chart animation.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **allPts** (All Points): Animate all points within the chart for this animation build step
    - **category** (Category): Animate a chart category for this animation build step
    - **gridLegend** (Grid and Legend): Animate the chart grid and legend for this animation build step
    - **ptInCategory** (Category Points): Animate a point in a chart category for this animation build step
    - **ptInSeries** (Series Points): Animate a point in a chart series for this animation build step
    - **series** (Series): Animate a chart series for this animation build step
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ChartBuildStep) is located in §A.4.1. end note]

## 20.1.10.14 ST_ColorSchemeIndex (Theme Color Reference)

=== "中文"

    对颜色方案中颜色的引用。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **accent1**（强调 1）：表示强调 1 颜色。
    - **accent2**（强调 2）：表示强调 2 颜色。
    - **accent3**（强调 3）：表示强调 3 颜色。
    - **accent4**（强调 4）：表示强调 4 颜色。
    - **accent5**（强调 5）：表示强调 5 颜色。
    - **accent6**（强调 6）：表示强调 6 颜色。
    - **dk1**（深色 1）：表示第一个深色。
    - **dk2**（深色 2）：表示第二个深色。
    - **folHlink**（已访问的超链接）：表示已访问的超链接颜色。
    - **hlink**（超链接）：表示超链接颜色。
    - **lt1**（浅色 1）：表示第一个浅色。
    - **lt2**（浅色 2）：表示第二个浅色。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ColorSchemeIndex) is located in §A.4.1. end note]

=== "英文"

    **ST_ColorSchemeIndex (Theme Color Reference)**

    A reference to a color in the color scheme.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **accent1** (Accent 1): Represents the accent 1 color.
    - **accent2** (Accent 2): Represents the accent 2 color.
    - **accent3** (Accent 3): Represents the accent 3 color.
    - **accent4** (Accent 4): Represents the accent 4 color.
    - **accent5** (Accent 5): Represents the accent 5 color.
    - **accent6** (Accent 6): Represents the accent 6 color.
    - **dk1** (Dark 1): Represents the first dark color.
    - **dk2** (Dark 2): Represents the second dark color.
    - **folHlink** (Followed Hyperlink): Represents the followed hyperlink color.
    - **hlink** (Hyperlink): Represents the hyperlink color.
    - **lt1** (Light 1): Represents the first light color.
    - **lt2** (Light 2): Represents the second light color.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ColorSchemeIndex) is located in §A.4.1. end note]

## 20.1.10.15 ST_CompoundLine (Compound Line Type)

=== "中文"

    这个简单类型指定了用于带有文本的线条（如下划线）的复合线类型。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **dbl**（双线）-- 双线，宽度相等
    - **sng**（单线）-- 单线，正常宽度
    - **thickThin**（粗细双线）-- 双线，一粗一细
    - **thinThick**（细粗双线）-- 双线，一细一粗
    - **tri**（细粗细三重线）-- 三条线，细、粗、细
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_CompoundLine) is located in §A.4.1. end note]

=== "英文"

    **ST_CompoundLine (Compound Line Type)**

    This simple type specifies the compound line type that is to be used for lines with text such as underlines.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
        
    This simple type is restricted to the values listed in the following table:

    - **dbl** (Double Lines) -- Double lines of equal width
    - **sng** (Single Line) -- Single line: one normal width
    - **thickThin** (Thick Thin Double Lines) -- Double lines: one thick, one thin
    - **thinThick** (Thin Thick Double Lines) -- Double lines: one thin, one thick
    - **tri** (Thin Thick Thin Triple Lines) -- Three lines: thin, thick, thin
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_CompoundLine) is located in §A.4.1. end note]

## 20.1.10.16 ST_Coordinate (坐标)

=== "中文"

    这个简单类型表示一维位置或长度，可以是：

    - EMUs。
    - 紧随其后为单位标识符的数字。

    这个简单类型是以下类型的联合体：

    - ST_CoordinateUnqualified 简单类型（§20.1.10.19）。
    - ST_UniversalMeasure 简单类型（§22.9.2.15）。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate) is located in §A.4.1.
    end note]

=== "英文"

    **ST_Coordinate (Coordinate)**

    This simple type represents a one dimensional position or length as either:

    - EMUs.
    - A number followed immediately by a unit identifier.

    This simple type is a union of the following types:

    - The ST_CoordinateUnqualified simple type (§20.1.10.19).
    - The ST_UniversalMeasure simple type (§22.9.2.15).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate) is located in §A.4.1.
    end note]

## 20.1.10.17 ST_Coordinate32 (坐标32位)

=== "中文"

    这个简单类型指定文档中的坐标。这可以用于测量或间距；其最大大小为 2147483647 EMUs。

    它的内容可以是：
    
    - 一个整数，其内容是以 EMUs（英文单位）为单位的测量值
    - 一个数字，紧跟着一个单位标识符
    
    这个简单类型是以下类型的联合体：
    
    - ST_Coordinate32Unqualified 简单类型（§20.1.10.18）。
    - ST_UniversalMeasure 简单类型（§22.9.2.15）。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate32) is located in §A.4.1. end note]

=== "英文"

    **ST_Coordinate32 (Coordinate Point)**

    This simple type specifies a coordinate within the document. This can be used for measurements or spacing; its maximum size is 2147483647 EMUs.

    Its contents can contain either:
    
    - A whole number, whose contents consist of a measurement in EMUs (English Metric Units)
    - A number immediately followed by a unit identifier
    
    This simple type is a union of the following types:
    
    - The ST_Coordinate32Unqualified simple type (§20.1.10.18).
    - The ST_UniversalMeasure simple type (§22.9.2.15).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate32) is located in §A.4.1. end note]

## 20.1.10.18 ST_Coordinate32Unqualified (坐标点)

=== "中文"

    这个简单类型指定了文档中的坐标。这可用于测量或空格，其最大大小要求是一个32位整数。

    这里使用的测量单位是 EMUs（英文度量单位）。
    
    这个简单类型的内容是对 W3C XML Schema int 数据类型的限制。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate32Unqualified) is located in §A.4.1. end note]

=== "英文"

    **ST_Coordinate32Unqualified (Coordinate Point)**

    This simple type specifies a coordinate within the document. This can be used for measurements or spacing with the maximum size requirement being a 32 bit integer.

    The units of measurement used here are EMUs (English Metric Units).

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Coordinate32Unqualified) is located in §A.4.1. end note]

## 20.1.10.19 ST_CoordinateUnqualified (Coordinate)

=== "中文"

    这个简单类型表示 EMUs 中的一维位置或长度。

    这个简单类型的内容是对 W3C XML Schema long 数据类型的限制。
    
    此简单类型还规定了以下限制：
    
    - 此简单类型的最小值大于或等于 -27273042329600。
    - 此简单类型的最大值小于或等于 27273042316900。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_CoordinateUnqualified) is located in §A.4.1. end note]

=== "英文"

    **ST_CoordinateUnqualified (Coordinate)**

    This simple type represents a one dimensional position or length in EMUs.

    This simple type's contents are a restriction of the W3C XML Schema long datatype.
    
    This simple type also specifies the following restrictions:
    
    - This simple type has a minimum value of greater than or equal to -27273042329600.
    - This simple type has a maximum value of less than or equal to 27273042316900.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_CoordinateUnqualified) is located in §A.4.1. end note]

## 20.1.10.20 ST_DgmBuildStep (Diagram 动画构建步骤)

=== "中文"

    这个简单类型指定了图表动画中的一个动画构建步骤。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    此简单类型仅限于以下表中列出的值：
    
    - **bg**（背景）：为此动画构建步骤对图表背景进行动画处理
    - **sp**（形状）：为此动画构建步骤对图表形状进行动画处理

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_DgmBuildStep) is located in §A.4.1. end note]

=== "英文"

    **ST_DgmBuildStep (Diagram Animation Build Steps)**

    This simple type specifies an animation build step within a diagram animation.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:
    
    - **bg** (Background): Animate the diagram background for this animation build step
    - **sp** (Shape): Animate a diagram shape for this animation build step

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_DgmBuildStep) is located in §A.4.1. end note]

## 20.1.10.21 ST_DrawingElementId (Drawing 元素标识符)

=== "中文"

    这个简单类型指定了每个绘图元素的唯一整数标识符。
    
    这个简单类型的内容是对 W3C XML Schema unsignedInt 数据类型的限制。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_DrawingElementId) is located in §A.4.1. end note]

=== "英文"

    **ST_DrawingElementId (Drawing Element ID)**

    This simple type specifies a unique integer identifier for each drawing element.

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_DrawingElementId) is located in §A.4.1. end note]

## 20.1.10.22 ST_EffectContainerType (效果容器类型)

=== "中文"

    这个简单类型确定了容器中效果之间的关系，可以是兄弟关系或树状关系。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型限制为以下表中列出的值：
    
    - **sib (Sibling)**
    
        每个效果都单独应用于父对象。
    
        [示例：如果父元素包含外部阴影和反射，则生成的效果是父对象周围的阴影和对象的反射。反射没有阴影。示例结束]
    
    - **tree (Tree)**
    
        每个效果都应用于前一个效果的结果。
    
        [示例：如果父元素包含外部阴影，然后是发光效果，阴影首先应用于父对象。然后，发光效果应用于阴影（而不是原始对象）。结果效果将是一个发光的阴影。示例结束]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_EffectContainerType) is located in §A.4.1. end note]

=== "英文"

    **ST_EffectContainerType (Effect Container Type)**

    This simple type determines the relationship between effects in a container, either sibling or tree.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **sib (Sibling)**

    :   Each effect is separately applied to the parent object.

        [Example: If the parent element contains an outer shadow and a reflection, the resulting effect is a shadow around the parent object and a reflection of the object. The reflection does not have a shadow. end example]
    
    **tree (Tree)**

    :   Each effect is applied to the result of the previous effect.
    
        [Example: If the parent element contains an outer shadow followed by a glow, the shadow is first applied to the parent object. Then, the glow is applied to the shadow (rather than the original object). The resulting effect would be a glowing shadow. end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_EffectContainerType) is located in §A.4.1. end note]

## 20.1.10.23 ST_FixedAngle (固定范围角度)

=== "中文"

    这个简单类型表示以 60000 分之一度为单位的固定范围角度。范围从（-90，90 度）。

    这个简单类型的内容是对 ST_Angle 数据类型（§20.1.10.3）的限制。
    
    这个简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于 -5400000。
    - 该简单类型的最大值小于 5400000。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FixedAngle) is located in §A.4.1. end note]

=== "英文"

    **ST_FixedAngle (Fixed Angle)**

    This simple type represents a fixed range angle in 60000ths of a degree. Range from (-90, 90 degrees).

    This simple type's contents are a restriction of the ST_Angle datatype (§20.1.10.3).
    
    This simple type also specifies the following restrictions:
    
    - This simple type has a minimum value of greater than -5400000.
    - This simple type has a maximum value of less than 5400000.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FixedAngle) is located in §A.4.1. end note]

## 20.1.10.24 ST_FixedPercentage (固定百分比)

=== "中文"

    这个简单类型表示从负一百到正一百百分比的固定百分比。有关详细信息，请参阅联合成员类型。这个简单类型是以下类型的联合体：

    - ST_FixedPercentage 简单类型（§22.9.2.3）。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FixedPercentage) is located in §A.4.1. end note]

=== "英文"

    **ST_FixedPercentage (Fixed Percentage)**

    This simple type represents a fixed percentage from negative one hundred to positive one hundred percent. See the union's member types for details. This simple type is a union of the following types:

    - The ST_FixedPercentage simple type (§22.9.2.3).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FixedPercentage) is located in §A.4.1. end note]

## 20.1.10.25 ST_FontCollectionIndex (字体集索引)

=== "中文"

    这个简单类型表示与样式相关联的字体之一。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型限制为以下表格中列出的值：
    
    - **major**（主要字体）：样式字体方案的主要字体。
    - **minor**（次要字体）：样式字体方案的次要字体。
    - **none**（无）：没有字体引用。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FontCollectionIndex) is located in §A.4.1. end note]

=== "英文"

    **ST_FontCollectionIndex (Font Collection Index)**

    This simple type represents one of the fonts associated with the style.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **major** (Major Font): The major font of the style's font scheme.
    - **minor** (Minor Font): The minor font of the style's font scheme.
    - **none** (None): No font reference.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FontCollectionIndex) is located in §A.4.1. end note]

## 20.1.10.26 ST_FOVAngle (视场角)

=== "中文"

    表示 60000 分之一度的正角。范围从 [0, 180] 度。

    这个简单类型的内容是对 ST_Angle 数据类型（§20.1.10.3）的限制。
    
    此简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于 0。
    - 该简单类型的最大值小于或等于 10800000。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FOVAngle) is located in §A.4.1. end note]

=== "英文"

    **ST_FOVAngle (Field of View Angle)**

    Represents a positive angle in 60000ths of a degree. Range from [0, 180] degrees.

    This simple type's contents are a restriction of the ST_Angle datatype (§20.1.10.3).

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 10800000.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FOVAngle) is located in §A.4.1. end note]

## 20.1.10.27 ST_GeomGuideFormula (几何指南公式属性)

=== "中文"

    这个简单类型指定了一个几何指南公式。
    
    该简单类型的内容是对W3C XML Schema字符串数据类型的限制。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_GeomGuideFormula) is located in §A.4.1. end note]

=== "英文"

    **ST_GeomGuideFormula (Geometry Guide Formula Properties)**

    This simple type specifies a geometry guide formula.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_GeomGuideFormula) is located in §A.4.1. end note]

## 20.1.10.28 ST_GeomGuideName (几何指南名称属性)

=== "中文"

    这个简单类型指定了一个几何指南名称。
    
    该简单类型的内容是对W3C XML Schema标记数据类型的限制。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_GeomGuideName) is located in §A.4.1. end note]

=== "英文"

    **ST_GeomGuideName (Geometry Guide Name Properties)**

    This simple type specifies a geometry guide name.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_GeomGuideName) is located in §A.4.1. end note]

## 20.1.10.29 ST_LightRigDirection (光照方向)

=== "中文"

    !!! info "译注"

        图片参见原pdf文档

    这个简单类型表示光源组相对于场景的位置。光源组本身可以由围绕给定形状的任何方向上的多个光源组成。这个简单类型定义了光源组作为整体的方向，而不是光源组内的单个光源。这意味着，因为光源组的方向是左侧，这并不保证光源来自形状的左侧，而是整体光源组的方向向左旋转。

    【例子】：考虑以下示例，将光源组的方向视觉表示为形状顶部：
    
    ![123](./imgs/aaa.png)
    
    在这个例子中，我们看到光源组定义了三个光源（都在由黑色圆形线表示的单个平面上）。在这个表示中定义的光源可以具有不同的强度，这意味着在这个例子中，光源3和光源2的效果可能更强烈（或甚至可能是不同的颜色）。
    
    下面的属性用于定义图像示例中使用的形状：
    
    - 圆角矩形形状
    - 三点光源组类型
    - 圆形倒角类型
    - 塑料材料类型
    - 由正交正面预设定义的相机类型
    - 倒角宽度和高度均等于190500
    
    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表中列出的值：
    
    **枚举**
    
    - **b (Bottom)**
    
        【例子：考虑来自底部的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **bl (Bottom Left)**
    
        【例子：考虑来自左下方的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **br (Bottom Right)**
    
        【例子：考虑来自右下方的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **l (Left)**
    
        【例子：考虑来自左侧的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **r (Right)**
    
        【例子：考虑来自右侧的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **t (Top)**
    
        【例子：考虑来自顶部的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **tl (Top Left)**
    
        【例子：考虑来自左上方的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    - **tr (Top Right)**
    
        【例子：考虑来自右上方的光照方向的以下示例： ![123](./imgs/aaa.png)】
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LightRigDirection) is located in §A.4.1. end note]

=== "英文"

    **ST_LightRigDirection (Light Rig Direction)**

    Represents the direction from which the light rig is positioned relative to the scene. The light rig, itself, can be made up of multiple lights in any orientation around a given shape. This simple type defines the orientation of the light rig as a whole, and not the individual lights within the rig. This means that because the direction of the light rig is left, that does not guarantee the light is coming from the left side of the shape, but rather the orientation of the rig as a whole is rotated to the left.
    
    [Example: Consider the following example as a visual representation of a light rig oriented from the top of the shape in the center:

    ![123](./imgs/aaa.png)

    In this example we see that the light rig defines three lights (all in a single plane as represented by the black circular line). The lights defined in this representation can all have different intensities, which means, for this example, Light 3 and Light 2 look to have a more intense effect (or could even be a different color) than Light 1. One can imagine rotating this rig to the so that Light 1 is to the right of the shape when the light rig direction is defined to be right. end example]
    
    The following properties were used to define the shape used in the image examples below:

    - Rounded rectangle shape
    - Three Point light rig type
    - Circle bevel type
    - Plastic material type
    - Camera type defined by the orthographicFront preset
    - Bevel width and height each equal to 190500
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **b (Bottom) **

    :   [Example: Consider the following example of a light direction from the bottom: ![123](./imgs/aaa.png) end example]

    **bl (Bottom Left)**

    :   [Example: Consider the following example of a light direction from the bottom left: ![123](./imgs/aaa.png) end example]

    **br (Bottom Right) **

    :   [Example: Consider the following example of a light direction from the bottom right: ![123](./imgs/aaa.png) end example]

    **l (Left) **

    :   [Example: Consider the following example of a light direction from the left: ![123](./imgs/aaa.png) end example]

    **r (Right)**

    :   [Example: Consider the following example of a light direction from the right: ![123](./imgs/aaa.png) end example]

    **t (Top)**

    :   [Example: Consider the following example of a light direction from the top: ![123](./imgs/aaa.png) end example]

    **tl (Top Left)**

    :   [Example: Consider the following example of a light direction from the top left: ![123](./imgs/aaa.png) end example]

    **tr (Top Right)**

    :   [Example: Consider the following example of a light direction from the top right: ![123](./imgs/aaa.png) end example]
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LightRigDirection) is located in §A.4.1. end note]

## 20.1.10.30 ST_LightRigType (光照类型)

=== "中文"

    **光源组类型**

    这个简单类型表示可以应用于形状的预设光源组。光源组表示一组相对于3D场景以特定方式定向的灯光。以下属性用于定义下面图像示例中使用的形状：
    
    - 圆角矩形形状
    - 圆形倒角类型
    - 暖色哑光材质类型
    - 由perspectiveContrastingRightFacing预设定义的相机类型
    - 倒角宽度和高度均为190500
    
    这个简单类型的内容是对W3C XML Schema令牌数据类型的限制。
    
    这个简单类型限制为以下表中列出的值：
    
    **枚举**
    
    - **balanced (平衡)**
        
        平衡 / Balanced
    
    - **brightRoom (明亮房间)**

        [示例：考虑将brightRoom光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **chilly (寒冷)**

        [示例：考虑将chilly光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **contrasting (对比)**

        [示例：考虑将contrasting光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **flat (平坦)**
        [示例：考虑将flat光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **flood (洪水)**

        [示例：考虑将flood光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **freezing (冰冻)**

        [示例：考虑将freezing光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **glow (发光)**

        [示例：考虑将glow光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **harsh (严苛)**

        [示例：考虑将harsh光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyFlat1 (传统平坦1)**

        [示例：考虑将legacyFlat1光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyFlat2 (传统平坦2)**

        [示例：考虑将legacyFlat2光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyFlat3 (传统平坦3)**

        [示例：考虑将legacyFlat3光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyFlat4 (传统平坦4)**

        [示例：考虑将legacyFlat4光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyHarsh1 (传统严苛1)**

        [示例：考虑将legacyHarsh1光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyHarsh2 (传统严苛2)**

        [示例：考虑将legacyHarsh2光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyHarsh3 (传统严苛3)**

        [示例：考虑将legacyHarsh3光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyHarsh4 (传统严苛4)**

        [示例：考虑将legacyHarsh4光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyNormal1 (传统正常1)**

        [示例：考虑将legacyNormal1光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyNormal2 (传统正常2)**

        [示例：考虑将legacyNormal2光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyNormal3 (传统正常3)**

        [示例：考虑将legacyNormal3光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **legacyNormal4 (传统正常4)**

        [示例：考虑将legacyNormal4光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **morning (早晨)**

        [示例：考虑将morning光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **soft (柔和)**

        [示例：考虑将soft光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    - **sunrise (日出)**

        [示例：考虑将sunrise光源组应用于基本形状的以下示例：![123](./imgs/aaa.png) 结束示例]
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LightRigType) is located in §A.4.1. end note]

=== "英文"

    **ST_LightRigType (Light Rig Type)**

    Represents a preset light right that can be applied to a shape. The light rig represents a group of lights oriented     in a specific way relative to a 3D scene. The following properties were used to define the shape used in the image examples below:
   
    - Rounded rectangle shape
    - Circle bevel type
    - Warm Matte material type
    - Camera type defined by the perspectiveContrastingRightFacing preset
    - Bevel width and height each equal to 190500

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**
    
    **balanced (Light Rig Enum ( Balanced )) **
    
    :   Balanced
    
    **brightRoom (Bright Room)**
    
    :   [Example: Consider the following example of the brightRoom light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **chilly (Chilly) **
    
    :   [Example: Consider the following example of the chilly light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **contrasting (Contrasting) **
    
    :   [Example: Consider the following example of the contrasting light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **flat (Flat) **
    
    :   [Example: Consider the following example of the flat light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **flood (Flood) **
    
    :   [Example: Consider the following example of the flood light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **freezing (Freezing) **
    
    :   [Example: Consider the following example of the freezing light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **glow (Glow) **
    
    :   [Example: Consider the following example of the glow light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **harsh (Harsh)  **
    
    :   [Example: Consider the following example of the harsh light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyFlat1 (Legacy Flat 1)**
    
    :   [Example: Consider the following example of the legacyFlat1 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyFlat2 (Legacy Flat 2)**
    
    :   [Example: Consider the following example of the legacyFlat2 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyFlat3 (Legacy Flat 3) **
    
    :   [Example: Consider the following example of the legacyFlat3 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyFlat4 (Legacy Flat 4) **
    
    :   [Example: Consider the following example of the legacyFlat4 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyHarsh1 (Legacy Harsh 1)**
    
    :   [Example: Consider the following example of the legacyHarsh1 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyHarsh2 (Legacy Harsh 2)**
    
    :   [Example: Consider the following example of the legacyHarsh2 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyHarsh3 (Legacy Harsh 3)**
    
    :   [Example: Consider the following example of the legacyHarsh3 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyHarsh4 (Legacy Harsh 4)**
    
    :   [Example: Consider the following example of the legacyHarsh4 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyNormal1 (Legacy Normal 1) **
    
    :   [Example: Consider the following example of the legacyNormal1 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyNormal2 (Legacy Normal 2) **
    
    :   [Example: Consider the following example of the legacyNormal2 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyNormal3 (Legacy Normal 3)**
    
    :   [Example: Consider the following example of the legacyNormal3 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **legacyNormal4 (Legacy Normal 4) **
    
    :   [Example: Consider the following example of the legacyNormal4 light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **morning (Morning)**
    
    :   [Example: Consider the following example of the morning light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **soft (Soft)**
    
    :   [Example: Consider the following example of the soft light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **sunrise (Sunrise)**
    
    :   [Example: Consider the following example of the sunrise light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **sunset (Sunset)**
    
    :   [Example: Consider the following example of the sunset light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **threePt (Three Point)**
    
    :   [Example: Consider the following example of the threePt light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    **twoPt (Two Point) **
    
    :   [Example: Consider the following example of the twoPt light rig applied to a basic shape: ![123](./imgs/aaa.png)  end example]
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LightRigType) is located in §A.4.1. end note]

## 20.1.10.31 ST_LineCap (线端点)

=== "中文"

    这个简单类型指定了如何对线的端点进行截断。这也会影响虚线的线段端点。

    这个简单类型的内容是对W3C XML Schema令牌数据类型的限制。
    
    这个简单类型限制为以下表中列出的值：
    
    - **flat**（平直线端点）：线段在端点结束。
    - **rnd**（圆形线端点）：圆形端点。半圆突出半条线宽。
    - **sq**（方形线端点）：方形端点。方形突出半条线宽。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineCap) is located in §A.4.1. end note]

=== "英文"

    **ST_LineCap (End Line Cap)**

    This simple type specifies how to cap the ends of lines. This also affects the ends of line segments for dashed lines.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:
    
    - **flat** (Flat Line Cap): Line ends at end point.
    - **rnd** (Round Line Cap): Rounded ends. Semi-circle protrudes by half line width.
    - **sq** (Square Line Cap): Square protrudes by half line width.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineCap) is located in §A.4.1. end note]

## 20.1.10.32 ST_LineEndLength (线端点长度)

=== "中文"

    !!! info "译注"

        pdf文档有图片示例

    这个简单类型表示线条结束装饰（例如箭头）相对于线条本身宽度的长度。
    
    【例】请参见下面的示例图像。这些示例具有箭头线端类型和中等线端宽度。【结束例】
    
    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。
    
    这个简单类型仅限于以下表中列出的值：
    
    - **lg**（大）：Large
    - **med**（中）：Medium
    - **sm**（小）：Small

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndLength) is located in §A.4.1. end note]

=== "英文"

    **ST_LineEndLength (Line End Length)**

    This simple type represents the length of the line end decoration (e.g., arrowhead) relative to the width of the line itself.
    
    [Example: See the example images below. These samples have an arrow line end type and medium line end width. end example]

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **lg** (Large): Large
    - **med** (Medium): Medium
    - **sm** (Small): Small

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndLength) is located in §A.4.1. end note]

## 20.1.10.33 ST_LineEndType (线端点类型)

=== "中文"

    这个简单类型表示出现在线条末端的形状装饰，例如箭头头部。

    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。

    这个简单类型仅限于以下表中列出的值：

    - **arrow**（箭头头部）：线箭头头部
    - **diamond**（菱形）：菱形
    - **none**（无）：无末端
    - **oval**（椭圆）：椭圆
    - **stealth**（隐形箭头）：隐形箭头头部
    - **triangle**（三角箭头头部）：三角箭头头部

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndType) is located in §A.4.1. end note]

    !!! info "译注"

        pdf文档有图片示例

=== "英文"

    **ST_LineEndType (Line End Type)**

    This simple type represents the shape decoration that appears at the ends of lines. For example, one choice is an arrow head.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **arrow** (Arrow Head):  Line arrow head
    - **diamond** (Diamond):  Diamond
    - **none** (None):  No end
    - **oval** (Oval):  Oval
    - **stealth** (Stealth Arrow):  Stealth arrow head
    - **triangle** (Triangle Arrow Head):  Triangle arrow head

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndType) is located in §A.4.1. end note]

## 20.1.10.34 ST_LineEndWidth (线端点宽端)

=== "中文"

    !!! info "译注"

        pdf文档有图片示例

    这个简单类型表示线条末端装饰（例如箭头头部）相对于线条本身宽度的宽度。

    [示例: 请参阅下面的示例图像。这些样本具有箭头线端类型和中等线端长度。示例结束]

    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。

    这个简单类型仅限于以下表中列出的值：

    - **lg**（大）：大
    - **med**（中）：中
    - **sm**（小）：小

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndWidth) is located in §A.4.1. end note]

=== "英文"

    **ST_LineEndWidth (Line End Width)**

    This simple type represents the width of the line end decoration (e.g., arrowhead) relative to the width of the line itself.

    [Example: See the example images below. These samples have an arrow line end type and medium line end length. end example]

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **lg** (Large): Large
    - **med** (Medium): Medium
    - **sm** (Small): Small

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineEndWidth) is located in §A.4.1. end note]

    !!! info "译注"

        pdf文档有图片示例

## 20.1.10.35 ST_LineWidth (线宽度)

=== "中文"

    这个简单类型指定了线条的宽度，以 EMUs（English Metric Units）为单位。1磅等于12700 EMUs。

    这个简单类型的内容是对 ST_Coordinate32Unqualified 数据类型（§20.1.10.18）的限制。
    
    这个简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于0。
    - 该简单类型的最大值小于或等于20116800。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineWidth) is located in §A.4.1. end note]

=== "英文"

    **ST_LineWidth (Line Width)**

    This simple type specifies the width of a line in EMUs. 1 pt = 12700 EMUs.

    This simple type's contents are a restriction of the ST_Coordinate32Unqualified datatype (§20.1.10.18).
    
    This simple type also specifies the following restrictions:
    
    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 20116800.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_LineWidth) is located in §A.4.1. end note]

## 20.1.10.36 ST_OnOffStyleType (样式类型开关)

=== "中文"

    这个简单类型表示是否应用样式属性。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **def**（默认）：遵循父级设置。对于主题化属性，遵循主题设置。对于非主题化属性，遵循属性继承链中的父级设置。
    - **off**（关闭）：属性被关闭。
    - **on**（打开）：属性被打开。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_OnOffStyleType) is located in §A.4.1. end note]

=== "英文"

    **ST_OnOffStyleType (On/Off Style Type)**

    This simple type represents whether a style property should be applied.
        
    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **def** (Default): Follow parent settings. For a themed property, follow the theme settings. For an unthemed property, follow the parent setting in the property inheritance chain.
    - **off** (Off): Property is off.
    - **on** (On): Property is on.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_OnOffStyleType) is located in §A.4.1. end note]

## 20.1.10.37 ST_PathFillMode (路径填充模式)

=== "中文"

    这个简单类型规定了路径填充的方式。路径的明暗变化允许根据用户的偏好对形状的特定部分进行轻或重的着色。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **darken**（加深路径填充）：指定相应的路径应该用较深的阴影颜色进行填充。
    - **darkenLess**（稍加深路径填充）：指定相应的路径应该用略微较深的阴影颜色进行填充。
    - **lighten**（加亮路径填充）：指定相应的路径应该用较浅的阴影颜色进行填充。
    - **lightenLess**（稍加亮路径填充）：指定相应的路径应该用略微较浅的阴影颜色进行填充。
    - **none**（无路径填充）：指定相应的路径不应填充任何颜色。
    - **norm**（正常路径填充）：指定相应的路径应该用正常阴影颜色进行填充。
    
    [注意：这个简单类型内容模型（ST_PathFillMode）的W3C XML Schema定义位于§A.4.1。末尾注释]

=== "英文"

    **ST_PathFillMode (Path Fill Mode)**

    This simple type specifies the manner in which a path should be filled. The lightening and darkening of a path allow for certain parts of the shape to be colored lighter of darker depending on user preference.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **darken** (Darken Path Fill): This specifies that the corresponding path should have a darker shaded color applied to it’s fill.
    - **darkenLess** (Darken Path Fill Less): This specifies that the corresponding path should have a slightly darker shaded color applied to it’s fill.
    - **lighten** (Lighten Path Fill): This specifies that the corresponding path should have a lightly shaded color applied to it’s fill.
    - **lightenLess** (Lighten Path Fill Less): This specifies that the corresponding path should have a slightly lighter shaded color applied to it’s fill.
    - **none** (No Path Fill): This specifies that the corresponding path should have no fill.
    - **norm** (Normal Path Fill): This specifies that the corresponding path should have a normally shaded color applied to it’s fill.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PathFillMode) is located in §A.4.1. end note]

## 20.1.10.38 ST_PathShadeType (路径阴影类型)

=== "中文"

    这个简单类型描述了用于路径渐变阴影的路径形状。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **circle**（圆形）：渐变沿着圆形路径
    - **rect**（矩形）：渐变沿着矩形路径
    - **shape**（形状）：渐变沿着形状路径
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PathShadeType) is located in §A.4.1. end note]

=== "英文"

    **ST_PathShadeType (Path Shade Type)**

    This simple type describes the shape of path to follow for a path gradient shade.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **circle** (Circle): Gradient follows a circular path
    - **rect** (Rectangle): Gradient follows a rectangular path
    - **shape** (Shape): Gradient follows the shape
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PathShadeType) is located in §A.4.1. end note]

## 20.1.10.39 ST_PenAlignment (对齐类型)

=== "中文"

    这个简单类型指定了用于文本主体的笔对齐类型。

    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **ctr**（居中对齐）：中心笔（绘制在路径描边的中心）。
    - **in**（插入对齐）：插入笔（笔对齐在路径边缘的内侧）。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PenAlignment) is located in §A.4.1. end note]

=== "英文"

    **ST_PenAlignment (Alignment Type)**

    This simple type specifies the Pen Alignment type for use within a text body.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table: 

    - **ctr** (Center Alignment): Center pen (line drawn at center of path stroke).
    - **in** (Inset Alignment): Inset pen (the pen is aligned on the inside of the edge of the path).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PenAlignment) is located in §A.4.1. end note]

## 20.1.10.40 ST_Percentage (百分比)

=== "中文"

    这个简单类型指定其内容将包含一个百分比值。有关详细信息，请参阅联合成员类型。

    这个简单类型是以下类型的联合体：
    
    - ST_Percentage 简单类型（§22.9.2.9）。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Percentage) is located in §A.4.1. end note]

=== "英文"

    **ST_Percentage (Percentage)**

    This simple type specifies that its contents will contain a percentage value. See the union's member types for details.

    This simple type is a union of the following types:

    - The ST_Percentage simple type (§22.9.2.9).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Percentage) is located in §A.4.1. end note]

## 20.1.10.41 ST_PitchFamily (字体的字符间距)

=== "中文"

    这个简单类型指定字体的字符间距。

    [注意：尽管类型名称是 ST_PitchFamily，但该属性的整数值指定具有较高4位字体族和较低4位字体字符间距的字体族。终止说明]

    这个简单类型的内容是对 W3C XML Schema 字节数据类型的限制。

    这个简单类型限制在以下表中列出的值：

    - **0x00**：默认字符间距 + 未知字体族
    - **0x01**：固定字符间距 + 未知字体族
    - **0x02**：可变字符间距 + 未知字体族
    - **0x10**：默认字符间距 + 罗马字体族
    - **0x11**：固定字符间距 + 罗马字体族
    - **0x12**：可变字符间距 + 罗马字体族
    - **0x20**：默认字符间距 + 瑞士字体族
    - **0x21**：固定字符间距 + 瑞士字体族
    - **0x22**：可变字符间距 + 瑞士字体族
    - **0x30**：默认字符间距 + 现代字体族
    - **0x31**：固定字符间距 + 现代字体族
    - **0x32**：可变字符间距 + 现代字体族
    - **0x40**：默认字符间距 + 草书字体族
    - **0x41**：固定字符间距 + 草书字体族
    - **0x42**：可变字符间距 + 草书字体族
    - **0x50**：默认字符间距 + 装饰字体族
    - **0x51**：固定字符间距 + 装饰字体族
    - **0x52**：可变字符间距 + 装饰字体族

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PitchFamily) is located in §A.3. end note]

=== "英文"

    **ST_PitchFamily (Pitch Family)**

    This simple type specifies a font pitch.

    [Note: Although the type name is ST_PitchFamily, the integer value of this attribute specifies the font family with the higher 4 bits and the font pitch with the lower 4 bits. end note]
    
    This simple type's contents are a restriction of the W3C XML Schema byte datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **0x00**: DEFAULT PITCH + UNKNOWN FONT FAMILY
    - **0x01**: FIXED PITCH + UNKNOWN FONT FAMILY
    - **0x02**: VARIABLE PITCH + UNKNOWN FONT FAMILY
    - **0x10**: DEFAULT PITCH + ROMAN FONT FAMILY
    - **0x11**: FIXED PITCH + ROMAN FONT FAMILY
    - **0x12**: VARIABLE PITCH + ROMAN FONT FAMILY
    - **0x20**: DEFAULT PITCH + SWISS FONT FAMILY
    - **0x21**: FIXED PITCH + SWISS FONT FAMILY
    - **0x22**: VARIABLE PITCH + SWISS FONT FAMILY
    - **0x30**: DEFAULT PITCH + MODERN FONT FAMILY
    - **0x31**: FIXED PITCH + MODERN FONT FAMILY
    - **0x32**: VARIABLE PITCH + MODERN FONT FAMILY
    - **0x40**: DEFAULT PITCH + SCRIPT FONT FAMILY
    - **0x41**: FIXED PITCH + SCRIPT FONT FAMILY
    - **0x42**: VARIABLE PITCH + SCRIPT FONT FAMILY
    - **0x50**: DEFAULT PITCH + DECORATIVE FONT FAMILY
    - **0x51**: FIXED PITCH + DECORATIVE FONT FAMILY
    - **0x52**: VARIABLE PITCH + DECORATIVE FONT FAMILY

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PitchFamily) is located in §A.3. end note]

## 20.1.10.42 ST_PositiveCoordinate (正坐标)

=== "中文"

    这个简单类型表示在 EMU 中的正位置或长度。

    这个简单类型的内容是对 W3C XML Schema 长整型数据类型的限制。
    
    这个简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于0。
    - 该简单类型的最大值小于或等于27273042316900。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveCoordinate) is located in §A.4.1. end note]

=== "英文"

    **ST_PositiveCoordinate (Positive Coordinate)**

    This simple type represents a positive position or length in EMUs.

    This simple type's contents are a restriction of the W3C XML Schema long datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 27273042316900.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveCoordinate) is located in §A.4.1. end note]

## 20.1.10.43 ST_PositiveCoordinate32 (正坐标点)

=== "中文"

    这个简单类型指定了一个最大为32位的正坐标点。

    此处使用的测量单位是 EMU（英语度量单位）。

    这个简单类型的内容是对 ST_Coordinate32Unqualified 数据类型的限制（§20.1.10.18）。

    此外，这个简单类型还指定了以下限制：

    - 该简单类型的最小值大于或等于0。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveCoordinate32) is located in §A.4.1. end note]

=== "英文"

    **ST_PositiveCoordinate32 (Positive Coordinate Point)**

    This simple type specifies the a positive coordinate point that has a maximum size of 32 bits.

    The units of measurement used here are EMUs (English Metric Units).
    
    This simple type's contents are a restriction of the ST_Coordinate32Unqualified datatype (§20.1.10.18).
    
    This simple type also specifies the following restrictions:
    
    - This simple type has a minimum value of greater than or equal to 0.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveCoordinate32) is located in §A.4.1. end note]

## 20.1.10.44 ST_PositiveFixedAngle (正角度)

=== "中文"

    这个简单类型表示一个正角度，以60000分之一度为单位。范围从 `[0, 360度)`。

    这个简单类型的内容是对 ST_Angle 数据类型（§20.1.10.3）的限制。
    
    此外，这个简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于0。
    - 该简单类型的最大值小于21600000。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveFixedAngle) is located in §A.4.1. end note]

=== "英文"

    **ST_PositiveFixedAngle (Positive Fixed Angle)**

    This simple type represents a positive angle in 60000ths of a degree. Range from `[0, 360 degrees)`.

    This simple type's contents are a restriction of the ST_Angle datatype (§20.1.10.3).

    This simple type also specifies the following restrictions:
    
    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than 21600000.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveFixedAngle) is located in §A.4.1. end note]

## 20.1.10.45 ST_PositiveFixedPercentage (正百分比值)

=== "中文"

    这个简单类型指定其内容将包含一个从零到百分之百的正百分比值。有关详细信息，请参阅该联合的成员类型。

    这个简单类型是以下类型的联合：

    - ST_PositiveFixedPercentage 简单类型（§22.9.2.10）。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveFixedPercentage) is
    located in §A.4.1. end note]

=== "英文"

    **ST_PositiveFixedPercentage (Positive Fixed Percentage)**

    This simple type specifies that its contents will contain a positive percentage value from zero through one hundred percent. See the union's member types for details.

    This simple type is a union of the following types:
    
    - The ST_PositiveFixedPercentage simple type (§22.9.2.10).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveFixedPercentage) is
    located in §A.4.1. end note]

## 20.1.10.46 ST_PositivePercentage (带符号的正百分比)

=== "中文"

    这个简单类型指定其内容将包含一个正百分比值。有关详细信息，请参阅该联合的成员类型。

    这个简单类型是以下类型的联合：
    
    - ST_PositivePercentage 简单类型（§22.9.2.11）。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositivePercentage) is located in §A.4.1. end note]

=== "英文"

    **ST_PositivePercentage (Positive Percentage Value with Sign)**

    This simple type specifies that its contents will contain a positive percentage value. See the union's member types for details.

    This simple type is a union of the following types:

    - The ST_PositivePercentage simple type (§22.9.2.11).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositivePercentage) is located in §A.4.1. end note]

## 20.1.10.47 ST_PresetCameraType (预设摄像机类型)

=== "中文"

    !!! info "译注"

        原文pdf查看图片

    这些枚举值表示不同的算法方法，用于设置所有摄像机属性，包括位置。以下示例图像都基于以下形状：

    ![123](./imgs/aaa.png)
    
    在这个图像中，我们可以看到该形状的摄像机正对着正面。
    
    这个简单类型的内容是对 W3C XML Schema token 数据类型的限制。
    
    这个简单类型受限于以下表中列出的值：

    **isometricBottomDown (Isometric Bottom Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricBottomUp (Isometric Bottom Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricLeftDown (Isometric Left Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricLeftUp (Isometric Left Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Left (Isometric Off Axis 1 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Right (Isometric Off Axis 1 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Top (Isometric Off Axis 1 Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Left (Isometric Off Axis 2 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Right (Isometric Off Axis 2 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Top (Isometric Off Axis 2 Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Bottom (Isometric Off Axis 3 Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Left (Isometric Off Axis 3 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Right (Isometric Off Axis 3 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Bottom (Isometric Off Axis 4 Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Left (Isometric Off Axis 4 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Right (Isometric Off Axis 4 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricRightDown (Isometric Right Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricRightUp (Isometric Right Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricTopDown (Isometric Top Down)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricTopUp (Isometric Top Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottom (Legacy Oblique Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottomLeft (Legacy Oblique Bottom Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottomRight (Legacy Oblique Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueFront (Legacy Oblique Front) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueLeft (Legacy Oblique Left) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueRight (Legacy Oblique Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTop (Legacy Oblique Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTopLeft (Legacy Oblique Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTopRight (Legacy Oblique Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottom (Legacy Perspective Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottomLeft (Legacy Perspective Bottom Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottomRight (Legacy Perspective Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveFront (Legacy Perspective Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveLeft (Legacy Perspective Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveRight (Legacy Perspective Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTop (Legacy Perspective Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTopLeft (Legacy Perspective Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTopRight (Legacy Perspective Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottom (Oblique Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottomLeft (Oblique Bottom Left) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottomRight (Oblique Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueLeft (Oblique Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueRight (Oblique Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTop (Oblique Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTopLeft (Oblique Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTopRight (Oblique Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **orthographicFront (Orthographic Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAbove (Orthographic Above)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAboveLeftFacing (Perspective Above Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAboveRightFacing (Perspective Above Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveBelow (Perspective Below)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveContrastingLeftFacing (Perspective Contrasting Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveContrastingRightFacing (Perspective Contrasting Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveFront (Perspective Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicExtremeLeftFacing (Perspective Heroic Extreme Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicExtremeRightFacing (Perspective Heroic Extreme Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicLeftFacing (Perspective Heroic Left Facing) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicRightFacing (Perspective Heroic Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveLeft (Perspective Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRelaxed (Perspective Relaxed)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRelaxedModerately (Perspective Relaxed Moderately)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRight (Perspective Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetCameraType) is located in §A.4.1. end note]

=== "英文"

    **ST_PresetCameraType (Preset Camera Type)**

    These enumeration values represent different algorithmic methods for setting all camera properties, including position. The following example images below are all based off the following shape:

    ![123](./imgs/aaa.png)

    In this image, we can see the shape has a camera pointing directly at the front face.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:
    
    **Enumeration**

    **isometricBottomDown (Isometric Bottom Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricBottomUp (Isometric Bottom Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricLeftDown (Isometric Left Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricLeftUp (Isometric Left Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Left (Isometric Off Axis 1 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Right (Isometric Off Axis 1 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis1Top (Isometric Off Axis 1 Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Left (Isometric Off Axis 2 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Right (Isometric Off Axis 2 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis2Top (Isometric Off Axis 2 Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Bottom (Isometric Off Axis 3 Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Left (Isometric Off Axis 3 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis3Right (Isometric Off Axis 3 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Bottom (Isometric Off Axis 4 Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Left (Isometric Off Axis 4 Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricOffAxis4Right (Isometric Off Axis 4 Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricRightDown (Isometric Right Down) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricRightUp (Isometric Right Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricTopDown (Isometric Top Down)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **isometricTopUp (Isometric Top Up)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottom (Legacy Oblique Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottomLeft (Legacy Oblique Bottom Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueBottomRight (Legacy Oblique Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueFront (Legacy Oblique Front) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueLeft (Legacy Oblique Left) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueRight (Legacy Oblique Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTop (Legacy Oblique Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTopLeft (Legacy Oblique Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyObliqueTopRight (Legacy Oblique Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottom (Legacy Perspective Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottomLeft (Legacy Perspective Bottom Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveBottomRight (Legacy Perspective Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveFront (Legacy Perspective Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveLeft (Legacy Perspective Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveRight (Legacy Perspective Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTop (Legacy Perspective Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTopLeft (Legacy Perspective Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **legacyPerspectiveTopRight (Legacy Perspective Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottom (Oblique Bottom)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottomLeft (Oblique Bottom Left) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueBottomRight (Oblique Bottom Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueLeft (Oblique Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueRight (Oblique Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTop (Oblique Top)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTopLeft (Oblique Top Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **obliqueTopRight (Oblique Top Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **orthographicFront (Orthographic Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAbove (Orthographic Above)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAboveLeftFacing (Perspective Above Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveAboveRightFacing (Perspective Above Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveBelow (Perspective Below)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveContrastingLeftFacing (Perspective Contrasting Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveContrastingRightFacing (Perspective Contrasting Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveFront (Perspective Front)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicExtremeLeftFacing (Perspective Heroic Extreme Left Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicExtremeRightFacing (Perspective Heroic Extreme Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicLeftFacing (Perspective Heroic Left Facing) **

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveHeroicRightFacing (Perspective Heroic Right Facing)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveLeft (Perspective Left)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRelaxed (Perspective Relaxed)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRelaxedModerately (Perspective Relaxed Moderately)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    **perspectiveRight (Perspective Right)**

    :   [Example: Consider the following example of the camera preset type: ![123](./imgs/aaa.png) end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetCameraType) is located in §A.4.1. end note]

## 20.1.10.48 ST_PresetColorVal (预设颜色值)

=== "中文"

    这个简单类型表示预设颜色值。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **aliceBlue** (爱丽丝蓝(Alice Blue) 预设颜色):  指定颜色RGB值为 (240,248,255)
    - **antiqueWhite** (古董白(Antique White) 预设颜色):  指定颜色RGB值为 (250,235,215)
    - **aqua** (水绿(Aqua) 预设颜色):  指定颜色RGB值为 (0,255,255)
    - **aquamarine** (碧绿(Aquamarine) 预设颜色):  指定颜色RGB值为 (127,255,212)
    - **azure** (天蓝(Azure) 预设颜色):  指定颜色RGB值为 (240,255,255)
    - **beige** (米色(Beige) 预设颜色):  指定颜色RGB值为 (245,245,220)
    - **bisque** (橙黄(Bisque) 预设颜色):  指定颜色RGB值为 (255,228,196)
    - **black** (黑色(Black) 预设颜色):  指定颜色RGB值为 (0,0,0)
    - **blanchedAlmond** (杏仁白(Blanched Almond) 预设颜色):  指定颜色RGB值为 (255,235,205)
    - **blue** (蓝色(Blue) 预设颜色):  指定颜色RGB值为 (0,0,255)
    - **blueViolet** (Blue Violet 预设颜色):  指定颜色RGB值为 (138,43,226)
    - **brown** (Brown 预设颜色):  指定颜色RGB值为 (165,42,42)
    - **burlyWood** (Burly Wood 预设颜色):  指定颜色RGB值为 (222,184,135)
    - **cadetBlue** (Cadet Blue 预设颜色):  指定颜色RGB值为 (95,158,160)
    - **chartreuse** (Chartreuse 预设颜色):  指定颜色RGB值为 (127,255,0)
    - **chocolate** (Chocolate 预设颜色):  指定颜色RGB值为 (210,105,30)
    - **coral** (Coral 预设颜色):  指定颜色RGB值为 (255,127,80)
    - **cornflowerBlue** (Cornflower Blue 预设颜色):  指定颜色RGB值为 (100,149,237)
    - **cornsilk** (Cornsilk 预设颜色):  指定颜色RGB值为 (255,248,220)
    - **crimson** (Crimson 预设颜色):  指定颜色RGB值为 (220,20,60)
    - **cyan** (Cyan 预设颜色):  指定颜色RGB值为 (0,255,255)
    - **darkBlue** (Dark Blue 预设颜色):  指定颜色RGB值为 (0,0,139)
    - **darkCyan** (Dark Cyan 预设颜色):  指定颜色RGB值为 (0,139,139)
    - **darkGoldenrod** (Dark Goldenrod 预设颜色):  指定颜色RGB值为 (184,134,11)
    - **darkGray** (Dark Gray 预设颜色):  指定颜色RGB值为 (169,169,169)
    - **darkGreen** (Dark Green 预设颜色):  指定颜色RGB值为 (0,100,0)
    - **darkGrey** (Dark Gray 预设颜色):  指定颜色RGB值为 (169,169,169)
    - **darkKhaki** (Dark Khaki 预设颜色):  指定颜色RGB值为 (189,183,107)
    - **darkMagenta** (Dark Magenta 预设颜色):  指定颜色RGB值为 (139,0,139)
    - **darkOliveGreen** (Dark Olive Green 预设颜色):  指定颜色RGB值为 (85,107,47)
    - **darkOrange** (Dark Orange 预设颜色):  指定颜色RGB值为 (255,140,0)
    - **darkOrchid** (Dark Orchid 预设颜色):  指定颜色RGB值为 (153,50,204)
    - **darkRed** (Dark Red 预设颜色):  指定颜色RGB值为 (139,0,0)
    - **darkSalmon** (Dark Salmon 预设颜色):  指定颜色RGB值为 (233,150,122)
    - **darkSeaGreen** (Dark Sea Green 预设颜色):  指定颜色RGB值为 (143,188,143)
    - **darkSlateBlue** (Dark Slate Blue 预设颜色):  指定颜色RGB值为 (72,61,139)
    - **darkSlateGray** (Dark Slate Gray 预设颜色):  指定颜色RGB值为 (47,79,79)
    - **darkSlateGrey** (Dark Slate Gray 预设颜色):  指定颜色RGB值为 (47,79,79)
    - **darkTurquoise** (Dark Turquoise 预设颜色):  指定颜色RGB值为 (0,206,209)
    - **darkViolet** (Dark Violet 预设颜色):  指定颜色RGB值为 (148,0,211)
    - **deepPink** (Deep Pink 预设颜色):  指定颜色RGB值为 (255,20,147)
    - **deepSkyBlue** (Deep Sky Blue 预设颜色):  指定颜色RGB值为 (0,191,255)
    - **dimGray** (Dim Gray 预设颜色):  指定颜色RGB值为 (105,105,105)
    - **dimGrey** (Dim Gray 预设颜色):  指定颜色RGB值为 (105,105,105)
    - **dkBlue** (Dark Blue 预设颜色):  指定颜色RGB值为 (0,0,139)
    - **dkCyan** (Dark Cyan 预设颜色):  指定颜色RGB值为 (0,139,139)
    - **dkGoldenrod** (Dark Goldenrod 预设颜色):  指定颜色RGB值为 (184,134,11)
    - **dkGray** (Dark Gray 预设颜色):  指定颜色RGB值为 (169,169,169)
    - **dkGreen** (Dark Green 预设颜色):  指定颜色RGB值为 (0,100,0)
    - **dkGrey** (Dark Gray 预设颜色):  指定颜色RGB值为 (169,169,169)
    - **dkKhaki** (Dark Khaki 预设颜色):  指定颜色RGB值为 (189,183,107)
    - **dkMagenta** (Dark Magenta 预设颜色):  指定颜色RGB值为 (139,0,139)
    - **dkOliveGreen** (Dark Olive Green 预设颜色):  指定颜色RGB值为 (85,107,47)
    - **dkOrange** (Dark Orange 预设颜色):  指定颜色RGB值为 (255,140,0)
    - **dkOrchid** (Dark Orchid 预设颜色):  指定颜色RGB值为 (153,50,204)
    - **dkRed** (Dark Red 预设颜色):  指定颜色RGB值为 (139,0,0)
    - **dkSalmon** (Dark Salmon 预设颜色):  指定颜色RGB值为 (233,150,122)
    - **dkSeaGreen** (Dark Sea Green 预设颜色):  指定颜色RGB值为 (143,188,139)
    - **dkSlateBlue** (Dark Slate Blue 预设颜色):  指定颜色RGB值为 (72,61,139)
    - **dkSlateGray** (Dark Slate Gray 预设颜色):  指定颜色RGB值为 (47,79,79)
    - **dkSlateGrey** (Dark Slate Gray 预设颜色):  指定颜色RGB值为 (47,79,79)
    - **dkTurquoise** (Dark Turquoise 预设颜色):  指定颜色RGB值为 (0,206,209)
    - **dkViolet** (Dark Violet 预设颜色):  指定颜色RGB值为 (148,0,211)
    - **dodgerBlue** (Dodger Blue 预设颜色):  指定颜色RGB值为 (30,144,255)
    - **firebrick** (Firebrick 预设颜色):  指定颜色RGB值为 (178,34,34)
    - **floralWhite** (Floral White 预设颜色):  指定颜色RGB值为 (255,250,240)
    - **forestGreen** (Forest Green 预设颜色):  指定颜色RGB值为 (34,139,34)
    - **fuchsia** (Fuchsia 预设颜色):  指定颜色RGB值为 (255,0,255)
    - **gainsboro** (Gainsboro 预设颜色):  指定颜色RGB值为 (220,220,220)
    - **ghostWhite** (Ghost White 预设颜色):  指定颜色RGB值为 (248,248,255)
    - **gold** (Gold 预设颜色):  指定颜色RGB值为 (255,215,0)
    - **goldenrod** (Goldenrod 预设颜色):  指定颜色RGB值为 (218,165,32)
    - **gray** (Gray 预设颜色):  指定颜色RGB值为 (128,128,128)
    - **green** (Green 预设颜色):  指定颜色RGB值为 (0,128,0)
    - **greenYellow** (Green Yellow 预设颜色):  指定颜色RGB值为 (173,255,47)
    - **grey** (Gray 预设颜色):  指定颜色RGB值为 (128,128,128)
    - **honeydew** (Honeydew 预设颜色):  指定颜色RGB值为 (240,255,240)
    - **hotPink** (Hot Pink 预设颜色):  指定颜色RGB值为 (255,105,180)
    - **indianRed** (Indian Red 预设颜色):  指定颜色RGB值为 (205,92,92)
    - **indigo** (Indigo 预设颜色):  指定颜色RGB值为 (75,0,130)
    - **ivory** (Ivory 预设颜色):  指定颜色RGB值为 (255,255,240)
    - **khaki** (Khaki 预设颜色):  指定颜色RGB值为 (240,230,140)
    - **lavender** (Lavender 预设颜色):  指定颜色RGB值为 (230,230,250)
    - **lavenderBlush** (Lavender Blush 预设颜色):  指定颜色RGB值为 (255,240,245)
    - **lawnGreen** (Lawn Green 预设颜色):  指定颜色RGB值为 (124,252,0)
    - **lemonChiffon** (Lemon Chiffon 预设颜色):  指定颜色RGB值为 (255,250,205)
    - **lightBlue** (Light Blue 预设颜色):  指定颜色RGB值为 (173,216,230)
    - **lightCoral** (Light Coral 预设颜色):  指定颜色RGB值为 (240,128,128)
    - **lightCyan** (Light Cyan 预设颜色):  指定颜色RGB值为 (224,255,255)
    - **lightGoldenrodYellow** (Light Goldenrod Yellow 预设颜色):  指定颜色RGB值为 (250,250,210)
    - **lightGray** (Light Gray 预设颜色):  指定颜色RGB值为 (211,211,211)
    - **lightGreen** (Light Green 预设颜色):  指定颜色RGB值为 (144,238,144)
    - **lightGrey** (Light Gray 预设颜色):  指定颜色RGB值为 (211,211,211)
    - **lightPink** (Light Pink 预设颜色):  指定颜色RGB值为 (255,182,193)
    - **lightSalmon** (Light Salmon 预设颜色):  指定颜色RGB值为 (255,160,122)
    - **lightSeaGreen** (Light Sea Green 预设颜色):  指定颜色RGB值为 (32,178,170)
    - **lightSkyBlue** (Light Sky Blue 预设颜色):  指定颜色RGB值为 (135,206,250)
    - **lightSlateGray** (Light Slate Gray 预设颜色):  指定颜色RGB值为 (119,136,153)
    - **lightSlateGrey** (Light Slate Gray 预设颜色):  指定颜色RGB值为 (119,136,153)
    - **lightSteelBlue** (Light Steel Blue 预设颜色):  指定颜色RGB值为 (176,196,222)
    - **lightYellow** (Light Yellow 预设颜色):  指定颜色RGB值为 (255,255,224)
    - **lime** (Lime 预设颜色):  指定颜色RGB值为 (0,255,0)
    - **limeGreen** (Lime Green 预设颜色):  指定颜色RGB值为 (50,205,50)
    - **linen** (Linen 预设颜色):  指定颜色RGB值为 (250,240,230)
    - **ltBlue** (Light Blue 预设颜色):  指定颜色RGB值为 (173,216,230)
    - **ltCoral** (Light Coral 预设颜色):  指定颜色RGB值为 (240,128,128)
    - **ltCyan** (Light Cyan 预设颜色):  指定颜色RGB值为 (224,255,255)
    - **ltGoldenrodYellow** (Light Goldenrod Yellow 预设颜色):  指定颜色RGB值为 (250,250,120)
    - **ltGray** (Light Gray 预设颜色):  指定颜色RGB值为 (211,211,211)
    - **ltGreen** (Light Green 预设颜色):  指定颜色RGB值为 (144,238,144)
    - **ltGrey** (Light Gray 预设颜色):  指定颜色RGB值为 (211,211,211)
    - **ltPink** (Light Pink 预设颜色):  指定颜色RGB值为 (255,182,193)
    - **ltSalmon** (Light Salmon 预设颜色):  指定颜色RGB值为 (255,160,122)
    - **ltSeaGreen** (Light Sea Green 预设颜色):  指定颜色RGB值为 (32,178,170)
    - **ltSkyBlue** (Light Sky Blue 预设颜色):  指定颜色RGB值为 (135,206,250)
    - **ltSlateGray** (Light Slate Gray 预设颜色):  指定颜色RGB值为 (119,136,153)
    - **ltSlateGrey** (Light Slate Gray 预设颜色):  指定颜色RGB值为 (119,136,153)
    - **ltSteelBlue** (Light Steel Blue 预设颜色):  指定颜色RGB值为 (176,196,222)
    - **ltYellow** (Light Yellow 预设颜色):  指定颜色RGB值为 (255,255,224)
    - **magenta** (Magenta 预设颜色):  指定颜色RGB值为 (255,0,255)
    - **maroon** (Maroon 预设颜色):  指定颜色RGB值为 (128,0,0)
    - **medAquamarine** (Medium Aquamarine 预设颜色):  指定颜色RGB值为 (102,205,170)
    - **medBlue** (Medium Blue 预设颜色):  指定颜色RGB值为 (0,0,205)
    - **mediumAquamarine** (Medium Aquamarine 预设颜色):  指定颜色RGB值为 (102,205,170)
    - **mediumBlue** (Medium Blue 预设颜色):  指定颜色RGB值为 (0,0,205)
    - **mediumOrchid** (Medium Orchid 预设颜色):  指定颜色RGB值为 (186,85,211)
    - **mediumPurple** (Medium Purple 预设颜色):  指定颜色RGB值为 (147,112,219)
    - **mediumSeaGreen** (Medium Sea Green 预设颜色):  指定颜色RGB值为 (60,179,113)
    - **mediumSlateBlue** (Medium Slate Blue 预设颜色):  指定颜色RGB值为 (123,104,238)
    - **mediumSpringGreen** (Medium Spring Green 预设颜色):  指定颜色RGB值为 (0,250,154)
    - **mediumTurquoise** (Medium Turquoise 预设颜色):  指定颜色RGB值为 (72,209,204)
    - **mediumVioletRed** (Medium Violet Red 预设颜色):  指定颜色RGB值为 (199,21,133)
    - **medOrchid** (Medium Orchid 预设颜色):  指定颜色RGB值为 (186,85,211)
    - **medPurple** (Medium Purple 预设颜色):  指定颜色RGB值为 (147,112,219)
    - **medSeaGreen** (Medium Sea Green 预设颜色):  指定颜色RGB值为 (60,179,113)
    - **medSlateBlue** (Medium Slate Blue 预设颜色):  指定颜色RGB值为 (123,104,238)
    - **medSpringGreen** (Medium Spring Green 预设颜色):  指定颜色RGB值为 (0,250,154)
    - **medTurquoise** (Medium Turquoise 预设颜色):  指定颜色RGB值为 (72,209,204)
    - **medVioletRed** (Medium Violet Red 预设颜色):  指定颜色RGB值为 (199,21,133)
    - **midnightBlue** (Midnight Blue 预设颜色):  指定颜色RGB值为 (25,25,112)
    - **mintCream** (Mint Cream 预设颜色):  指定颜色RGB值为 (245,255,250)
    - **mistyRose** (Misty Rose 预设颜色):  指定颜色RGB值为 (255,228,225)
    - **moccasin** (Moccasin 预设颜色):  指定颜色RGB值为 (255,228,181)
    - **navajoWhite** (Navajo White 预设颜色):  指定颜色RGB值为 (255,222,173)
    - **navy** (Navy 预设颜色):  指定颜色RGB值为 (0,0,128)
    - **oldLace** (Old Lace 预设颜色):  指定颜色RGB值为 (253,245,230)
    - **olive** (Olive 预设颜色):  指定颜色RGB值为 (128,128,0)
    - **oliveDrab** (Olive Drab 预设颜色):  指定颜色RGB值为 (107,142,35)
    - **orange** (Orange 预设颜色):  指定颜色RGB值为 (255,165,0)
    - **orangeRed** (Orange Red 预设颜色):  指定颜色RGB值为 (255,69,0)
    - **orchid** (Orchid 预设颜色):  指定颜色RGB值为 (218,112,214)
    - **paleGoldenrod** (Pale Goldenrod 预设颜色):  指定颜色RGB值为 (238,232,170)
    - **paleGreen** (Pale Green 预设颜色):  指定颜色RGB值为 (152,251,152)
    - **paleTurquoise** (Pale Turquoise 预设颜色):  指定颜色RGB值为 (175,238,238)
    - **paleVioletRed** (Pale Violet Red 预设颜色):  指定颜色RGB值为 (219,112,147)
    - **papayaWhip** (Papaya Whip 预设颜色):  指定颜色RGB值为 (255,239,213)
    - **peachPuff** (Peach Puff 预设颜色):  指定颜色RGB值为 (255,218,185)
    - **peru** (Peru 预设颜色):  指定颜色RGB值为 (205,133,63)
    - **pink** (Pink 预设颜色):  指定颜色RGB值为 (255,192,203)
    - **plum** (Plum 预设颜色):  指定颜色RGB值为 (221,160,221)
    - **powderBlue** (Powder Blue 预设颜色):  指定颜色RGB值为 (176,224,230)
    - **purple** (Purple 预设颜色):  指定颜色RGB值为 (128,0,128)
    - **red** (Red 预设颜色):  指定颜色RGB值为 (255,0,0)
    - **rosyBrown** (Rosy Brown 预设颜色):  指定颜色RGB值为 (188,143,143)
    - **royalBlue** (Royal Blue 预设颜色):  指定颜色RGB值为 (65,105,225)
    - **saddleBrown** (Saddle Brown 预设颜色):  指定颜色RGB值为 (139,69,19)
    - **salmon** (Salmon 预设颜色):  指定颜色RGB值为 (250,128,114)
    - **sandyBrown** (Sandy Brown 预设颜色):  指定颜色RGB值为 (244,164,96)
    - **seaGreen** (Sea Green 预设颜色):  指定颜色RGB值为 (46,139,87)
    - **seaShell** (Sea Shell 预设颜色):  指定颜色RGB值为 (255,245,238)
    - **sienna** (Sienna 预设颜色):  指定颜色RGB值为 (160,82,45)
    - **silver** (Silver 预设颜色):  指定颜色RGB值为 (192,192,192)
    - **skyBlue** (Sky Blue 预设颜色):  指定颜色RGB值为 (135,206,235)
    - **slateBlue** (Slate Blue 预设颜色):  指定颜色RGB值为 (106,90,205)
    - **slateGray** (Slate Gray 预设颜色):  指定颜色RGB值为 (112,128,144)
    - **slateGrey** (Slate Gray 预设颜色):  指定颜色RGB值为 (112,128,144)
    - **snow** (Snow 预设颜色):  指定颜色RGB值为 (255,250,250)
    - **springGreen** (Spring Green 预设颜色):  指定颜色RGB值为 (0,255,127)
    - **steelBlue** (Steel Blue 预设颜色):  指定颜色RGB值为 (70,130,180)
    - **tan** (Tan 预设颜色):  指定颜色RGB值为 (210,180,140)
    - **teal** (Teal 预设颜色):  指定颜色RGB值为 (0,128,128)
    - **thistle** (Thistle 预设颜色):  指定颜色RGB值为 (216,191,216)
    - **tomato** (Tomato 预设颜色):  指定颜色RGB值为 (255,99,71)
    - **turquoise** (Turquoise 预设颜色):  指定颜色RGB值为 (64,224,208)
    - **violet** (Violet 预设颜色):  指定颜色RGB值为 (238,130,238)
    - **wheat** (Wheat 预设颜色):  指定颜色RGB值为 (245,222,179)
    - **white** (White 预设颜色):  指定颜色RGB值为 (255,255,255)
    - **whiteSmoke** (White Smoke 预设颜色):  指定颜色RGB值为 (245,245,245)
    - **yellow** (Yellow 预设颜色):  指定颜色RGB值为 (255,255,0)
    - **yellowGreen** (Yellow Green 预设颜色):  指定颜色RGB值为 (154,205,50)

    [注意：这个简单类型内容模型（ST_PresetColorVal）的W3C XML Schema定义位于§A.4.1。末尾注释]

=== "英文"

    **ST_PresetColorVal (Preset Color Value)**

    This simple type represents a preset color value.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:
    
    - **aliceBlue** (Alice Blue Preset Color):  Specifies a color with RGB value (240,248,255)
    - **antiqueWhite** (Antique White Preset Color):  Specifies a color with RGB value (250,235,215)
    - **aqua** (Aqua Preset Color):  Specifies a color with RGB value (0,255,255)
    - **aquamarine** (Aquamarine Preset Color):  Specifies a color with RGB value (127,255,212)
    - **azure** (Azure Preset Color):  Specifies a color with RGB value (240,255,255)
    - **beige** (Beige Preset Color):  Specifies a color with RGB value (245,245,220)
    - **bisque** (Bisque Preset Color):  Specifies a color with RGB value (255,228,196)
    - **black** (Black Preset Color):  Specifies a color with RGB value (0,0,0)
    - **blanchedAlmond** (Blanched Almond Preset Color):  Specifies a color with RGB value (255,235,205)
    - **blue** (Blue Preset Color):  Specifies a color with RGB value (0,0,255)
    - **blueViolet** (Blue Violet Preset Color):  Specifies a color with RGB value (138,43,226)
    - **brown** (Brown Preset Color):  Specifies a color with RGB value (165,42,42)
    - **burlyWood** (Burly Wood Preset Color):  Specifies a color with RGB value (222,184,135)
    - **cadetBlue** (Cadet Blue Preset Color):  Specifies a color with RGB value (95,158,160)
    - **chartreuse** (Chartreuse Preset Color):  Specifies a color with RGB value (127,255,0)
    - **chocolate** (Chocolate Preset Color):  Specifies a color with RGB value (210,105,30)
    - **coral** (Coral Preset Color):  Specifies a color with RGB value (255,127,80)
    - **cornflowerBlue** (Cornflower Blue Preset Color):  Specifies a color with RGB value (100,149,237)
    - **cornsilk** (Cornsilk Preset Color):  Specifies a color with RGB value (255,248,220)
    - **crimson** (Crimson Preset Color):  Specifies a color with RGB value (220,20,60)
    - **cyan** (Cyan Preset Color):  Specifies a color with RGB value (0,255,255)
    - **darkBlue** (Dark Blue Preset Color):  Specifies a color with RGB value (0,0,139)
    - **darkCyan** (Dark Cyan Preset Color):  Specifies a color with RGB value (0,139,139)
    - **darkGoldenrod** (Dark Goldenrod Preset Color):  Specifies a color with RGB value (184,134,11)
    - **darkGray** (Dark Gray Preset Color):  Specifies a color with RGB value (169,169,169)
    - **darkGreen** (Dark Green Preset Color):  Specifies a color with RGB value (0,100,0)
    - **darkGrey** (Dark Gray Preset Color):  Specifies a color with RGB value (169,169,169)
    - **darkKhaki** (Dark Khaki Preset Color):  Specifies a color with RGB value (189,183,107)
    - **darkMagenta** (Dark Magenta Preset Color):  Specifies a color with RGB value (139,0,139)
    - **darkOliveGreen** (Dark Olive Green Preset Color):  Specifies a color with RGB value (85,107,47)
    - **darkOrange** (Dark Orange Preset Color):  Specifies a color with RGB value (255,140,0)
    - **darkOrchid** (Dark Orchid Preset Color):  Specifies a color with RGB value (153,50,204)
    - **darkRed** (Dark Red Preset Color):  Specifies a color with RGB value (139,0,0)
    - **darkSalmon** (Dark Salmon Preset Color):  Specifies a color with RGB value (233,150,122)
    - **darkSeaGreen** (Dark Sea Green Preset Color):  Specifies a color with RGB value (143,188,143)
    - **darkSlateBlue** (Dark Slate Blue Preset Color):  Specifies a color with RGB value (72,61,139)
    - **darkSlateGray** (Dark Slate Gray Preset Color):  Specifies a color with RGB value (47,79,79)
    - **darkSlateGrey** (Dark Slate Gray Preset Color):  Specifies a color with RGB value (47,79,79)
    - **darkTurquoise** (Dark Turquoise Preset Color):  Specifies a color with RGB value (0,206,209)
    - **darkViolet** (Dark Violet Preset Color):  Specifies a color with RGB value (148,0,211)
    - **deepPink** (Deep Pink Preset Color):  Specifies a color with RGB value (255,20,147)
    - **deepSkyBlue** (Deep Sky Blue Preset Color):  Specifies a color with RGB value (0,191,255)
    - **dimGray** (Dim Gray Preset Color):  Specifies a color with RGB value (105,105,105)
    - **dimGrey** (Dim Gray Preset Color):  Specifies a color with RGB value (105,105,105)
    - **dkBlue** (Dark Blue Preset Color):  Specifies a color with RGB value (0,0,139)
    - **dkCyan** (Dark Cyan Preset Color):  Specifies a color with RGB value (0,139,139)
    - **dkGoldenrod** (Dark Goldenrod Preset Color):  Specifies a color with RGB value (184,134,11)
    - **dkGray** (Dark Gray Preset Color):  Specifies a color with RGB value (169,169,169)
    - **dkGreen** (Dark Green Preset Color):  Specifies a color with RGB value (0,100,0)
    - **dkGrey** (Dark Gray Preset Color):  Specifies a color with RGB value (169,169,169)
    - **dkKhaki** (Dark Khaki Preset Color):  Specifies a color with RGB value (189,183,107)
    - **dkMagenta** (Dark Magenta Preset Color):  Specifies a color with RGB value (139,0,139)
    - **dkOliveGreen** (Dark Olive Green Preset Color):  Specifies a color with RGB value (85,107,47)
    - **dkOrange** (Dark Orange Preset Color):  Specifies a color with RGB value (255,140,0)
    - **dkOrchid** (Dark Orchid Preset Color):  Specifies a color with RGB value (153,50,204)
    - **dkRed** (Dark Red Preset Color):  Specifies a color with RGB value (139,0,0)
    - **dkSalmon** (Dark Salmon Preset Color):  Specifies a color with RGB value (233,150,122)
    - **dkSeaGreen** (Dark Sea Green Preset Color):  Specifies a color with RGB value (143,188,139)
    - **dkSlateBlue** (Dark Slate Blue Preset Color):  Specifies a color with RGB value (72,61,139)
    - **dkSlateGray** (Dark Slate Gray Preset Color):  Specifies a color with RGB value (47,79,79)
    - **dkSlateGrey** (Dark Slate Gray Preset Color):  Specifies a color with RGB value (47,79,79)
    - **dkTurquoise** (Dark Turquoise Preset Color):  Specifies a color with RGB value (0,206,209)
    - **dkViolet** (Dark Violet Preset Color):  Specifies a color with RGB value (148,0,211)
    - **dodgerBlue** (Dodger Blue Preset Color):  Specifies a color with RGB value (30,144,255)
    - **firebrick** (Firebrick Preset Color):  Specifies a color with RGB value (178,34,34)
    - **floralWhite** (Floral White Preset Color):  Specifies a color with RGB value (255,250,240)
    - **forestGreen** (Forest Green Preset Color):  Specifies a color with RGB value (34,139,34)
    - **fuchsia** (Fuchsia Preset Color):  Specifies a color with RGB value (255,0,255)
    - **gainsboro** (Gainsboro Preset Color):  Specifies a color with RGB value (220,220,220)
    - **ghostWhite** (Ghost White Preset Color):  Specifies a color with RGB value (248,248,255)
    - **gold** (Gold Preset Color):  Specifies a color with RGB value (255,215,0)
    - **goldenrod** (Goldenrod Preset Color):  Specifies a color with RGB value (218,165,32)
    - **gray** (Gray Preset Color):  Specifies a color with RGB value (128,128,128)
    - **green** (Green Preset Color):  Specifies a color with RGB value (0,128,0)
    - **greenYellow** (Green Yellow Preset Color):  Specifies a color with RGB value (173,255,47)
    - **grey** (Gray Preset Color):  Specifies a color with RGB value (128,128,128)
    - **honeydew** (Honeydew Preset Color):  Specifies a color with RGB value (240,255,240)
    - **hotPink** (Hot Pink Preset Color):  Specifies a color with RGB value (255,105,180)
    - **indianRed** (Indian Red Preset Color):  Specifies a color with RGB value (205,92,92)
    - **indigo** (Indigo Preset Color):  Specifies a color with RGB value (75,0,130)
    - **ivory** (Ivory Preset Color):  Specifies a color with RGB value (255,255,240)
    - **khaki** (Khaki Preset Color):  Specifies a color with RGB value (240,230,140)
    - **lavender** (Lavender Preset Color):  Specifies a color with RGB value (230,230,250)
    - **lavenderBlush** (Lavender Blush Preset Color):  Specifies a color with RGB value (255,240,245)
    - **lawnGreen** (Lawn Green Preset Color):  Specifies a color with RGB value (124,252,0)
    - **lemonChiffon** (Lemon Chiffon Preset Color):  Specifies a color with RGB value (255,250,205)
    - **lightBlue** (Light Blue Preset Color):  Specifies a color with RGB value (173,216,230)
    - **lightCoral** (Light Coral Preset Color):  Specifies a color with RGB value (240,128,128)
    - **lightCyan** (Light Cyan Preset Color):  Specifies a color with RGB value (224,255,255)
    - **lightGoldenrodYellow** (Light Goldenrod Yellow Preset Color):  Specifies a color with RGB value (250,250,210)
    - **lightGray** (Light Gray Preset Color):  Specifies a color with RGB value (211,211,211)
    - **lightGreen** (Light Green Preset Color):  Specifies a color with RGB value (144,238,144)
    - **lightGrey** (Light Gray Preset Color):  Specifies a color with RGB value (211,211,211)
    - **lightPink** (Light Pink Preset Color):  Specifies a color with RGB value (255,182,193)
    - **lightSalmon** (Light Salmon Preset Color):  Specifies a color with RGB value (255,160,122)
    - **lightSeaGreen** (Light Sea Green Preset Color):  Specifies a color with RGB value (32,178,170)
    - **lightSkyBlue** (Light Sky Blue Preset Color):  Specifies a color with RGB value (135,206,250)
    - **lightSlateGray** (Light Slate Gray Preset Color):  Specifies a color with RGB value (119,136,153)
    - **lightSlateGrey** (Light Slate Gray Preset Color):  Specifies a color with RGB value (119,136,153)
    - **lightSteelBlue** (Light Steel Blue Preset Color):  Specifies a color with RGB value (176,196,222)
    - **lightYellow** (Light Yellow Preset Color):  Specifies a color with RGB value (255,255,224)
    - **lime** (Lime Preset Color):  Specifies a color with RGB value (0,255,0)
    - **limeGreen** (Lime Green Preset Color):  Specifies a color with RGB value (50,205,50)
    - **linen** (Linen Preset Color):  Specifies a color with RGB value (250,240,230)
    - **ltBlue** (Light Blue Preset Color):  Specifies a color with RGB value (173,216,230)
    - **ltCoral** (Light Coral Preset Color):  Specifies a color with RGB value (240,128,128)
    - **ltCyan** (Light Cyan Preset Color):  Specifies a color with RGB value (224,255,255)
    - **ltGoldenrodYellow** (Light Goldenrod Yellow Preset Color):  Specifies a color with RGB value (250,250,120)
    - **ltGray** (Light Gray Preset Color):  Specifies a color with RGB value (211,211,211)
    - **ltGreen** (Light Green Preset Color):  Specifies a color with RGB value (144,238,144)
    - **ltGrey** (Light Gray Preset Color):  Specifies a color with RGB value (211,211,211)
    - **ltPink** (Light Pink Preset Color):  Specifies a color with RGB value (255,182,193)
    - **ltSalmon** (Light Salmon Preset Color):  Specifies a color with RGB value (255,160,122)
    - **ltSeaGreen** (Light Sea Green Preset Color):  Specifies a color with RGB value (32,178,170)
    - **ltSkyBlue** (Light Sky Blue Preset Color):  Specifies a color with RGB value (135,206,250)
    - **ltSlateGray** (Light Slate Gray Preset Color):  Specifies a color with RGB value (119,136,153)
    - **ltSlateGrey** (Light Slate Gray Preset Color):  Specifies a color with RGB value (119,136,153)
    - **ltSteelBlue** (Light Steel Blue Preset Color):  Specifies a color with RGB value (176,196,222)
    - **ltYellow** (Light Yellow Preset Color):  Specifies a color with RGB value (255,255,224)
    - **magenta** (Magenta Preset Color):  Specifies a color with RGB value (255,0,255)
    - **maroon** (Maroon Preset Color):  Specifies a color with RGB value (128,0,0)
    - **medAquamarine** (Medium Aquamarine Preset Color):  Specifies a color with RGB value (102,205,170)
    - **medBlue** (Medium Blue Preset Color):  Specifies a color with RGB value (0,0,205)
    - **mediumAquamarine** (Medium Aquamarine Preset Color):  Specifies a color with RGB value (102,205,170)
    - **mediumBlue** (Medium Blue Preset Color):  Specifies a color with RGB value (0,0,205)
    - **mediumOrchid** (Medium Orchid Preset Color):  Specifies a color with RGB value (186,85,211)
    - **mediumPurple** (Medium Purple Preset Color):  Specifies a color with RGB value (147,112,219)
    - **mediumSeaGreen** (Medium Sea Green Preset Color):  Specifies a color with RGB value (60,179,113)
    - **mediumSlateBlue** (Medium Slate Blue Preset Color):  Specifies a color with RGB value (123,104,238)
    - **mediumSpringGreen** (Medium Spring Green Preset Color):  Specifies a color with RGB value (0,250,154)
    - **mediumTurquoise** (Medium Turquoise Preset Color):  Specifies a color with RGB value (72,209,204)
    - **mediumVioletRed** (Medium Violet Red Preset Color):  Specifies a color with RGB value (199,21,133)
    - **medOrchid** (Medium Orchid Preset Color):  Specifies a color with RGB value (186,85,211)
    - **medPurple** (Medium Purple Preset Color):  Specifies a color with RGB value (147,112,219)
    - **medSeaGreen** (Medium Sea Green Preset Color):  Specifies a color with RGB value (60,179,113)
    - **medSlateBlue** (Medium Slate Blue Preset Color):  Specifies a color with RGB value (123,104,238)
    - **medSpringGreen** (Medium Spring Green Preset Color):  Specifies a color with RGB value (0,250,154)
    - **medTurquoise** (Medium Turquoise Preset Color):  Specifies a color with RGB value (72,209,204)
    - **medVioletRed** (Medium Violet Red Preset Color):  Specifies a color with RGB value (199,21,133)
    - **midnightBlue** (Midnight Blue Preset Color):  Specifies a color with RGB value (25,25,112)
    - **mintCream** (Mint Cream Preset Color):  Specifies a color with RGB value (245,255,250)
    - **mistyRose** (Misty Rose Preset Color):  Specifies a color with RGB value (255,228,225)
    - **moccasin** (Moccasin Preset Color):  Specifies a color with RGB value (255,228,181)
    - **navajoWhite** (Navajo White Preset Color):  Specifies a color with RGB value (255,222,173)
    - **navy** (Navy Preset Color):  Specifies a color with RGB value (0,0,128)
    - **oldLace** (Old Lace Preset Color):  Specifies a color with RGB value (253,245,230)
    - **olive** (Olive Preset Color):  Specifies a color with RGB value (128,128,0)
    - **oliveDrab** (Olive Drab Preset Color):  Specifies a color with RGB value (107,142,35)
    - **orange** (Orange Preset Color):  Specifies a color with RGB value (255,165,0)
    - **orangeRed** (Orange Red Preset Color):  Specifies a color with RGB value (255,69,0)
    - **orchid** (Orchid Preset Color):  Specifies a color with RGB value (218,112,214)
    - **paleGoldenrod** (Pale Goldenrod Preset Color):  Specifies a color with RGB value (238,232,170)
    - **paleGreen** (Pale Green Preset Color):  Specifies a color with RGB value (152,251,152)
    - **paleTurquoise** (Pale Turquoise Preset Color):  Specifies a color with RGB value (175,238,238)
    - **paleVioletRed** (Pale Violet Red Preset Color):  Specifies a color with RGB value (219,112,147)
    - **papayaWhip** (Papaya Whip Preset Color):  Specifies a color with RGB value (255,239,213)
    - **peachPuff** (Peach Puff Preset Color):  Specifies a color with RGB value (255,218,185)
    - **peru** (Peru Preset Color):  Specifies a color with RGB value (205,133,63)
    - **pink** (Pink Preset Color):  Specifies a color with RGB value (255,192,203)
    - **plum** (Plum Preset Color):  Specifies a color with RGB value (221,160,221)
    - **powderBlue** (Powder Blue Preset Color):  Specifies a color with RGB value (176,224,230)
    - **purple** (Purple Preset Color):  Specifies a color with RGB value (128,0,128)
    - **red** (Red Preset Color):  Specifies a color with RGB value (255,0,0)
    - **rosyBrown** (Rosy Brown Preset Color):  Specifies a color with RGB value (188,143,143)
    - **royalBlue** (Royal Blue Preset Color):  Specifies a color with RGB value (65,105,225)
    - **saddleBrown** (Saddle Brown Preset Color):  Specifies a color with RGB value (139,69,19)
    - **salmon** (Salmon Preset Color):  Specifies a color with RGB value (250,128,114)
    - **sandyBrown** (Sandy Brown Preset Color):  Specifies a color with RGB value (244,164,96)
    - **seaGreen** (Sea Green Preset Color):  Specifies a color with RGB value (46,139,87)
    - **seaShell** (Sea Shell Preset Color):  Specifies a color with RGB value (255,245,238)
    - **sienna** (Sienna Preset Color):  Specifies a color with RGB value (160,82,45)
    - **silver** (Silver Preset Color):  Specifies a color with RGB value (192,192,192)
    - **skyBlue** (Sky Blue Preset Color):  Specifies a color with RGB value (135,206,235)
    - **slateBlue** (Slate Blue Preset Color):  Specifies a color with RGB value (106,90,205)
    - **slateGray** (Slate Gray Preset Color):  Specifies a color with RGB value (112,128,144)
    - **slateGrey** (Slate Gray Preset Color):  Specifies a color with RGB value (112,128,144)
    - **snow** (Snow Preset Color):  Specifies a color with RGB value (255,250,250)
    - **springGreen** (Spring Green Preset Color):  Specifies a color with RGB value (0,255,127)
    - **steelBlue** (Steel Blue Preset Color):  Specifies a color with RGB value (70,130,180)
    - **tan** (Tan Preset Color):  Specifies a color with RGB value (210,180,140)
    - **teal** (Teal Preset Color):  Specifies a color with RGB value (0,128,128)
    - **thistle** (Thistle Preset Color):  Specifies a color with RGB value (216,191,216)
    - **tomato** (Tomato Preset Color):  Specifies a color with RGB value (255,99,71)
    - **turquoise** (Turquoise Preset Color):  Specifies a color with RGB value (64,224,208)
    - **violet** (Violet Preset Color):  Specifies a color with RGB value (238,130,238)
    - **wheat** (Wheat Preset Color):  Specifies a color with RGB value (245,222,179)
    - **white** (White Preset Color):  Specifies a color with RGB value (255,255,255)
    - **whiteSmoke** (White Smoke Preset Color):  Specifies a color with RGB value (245,245,245)
    - **yellow** (Yellow Preset Color):  Specifies a color with RGB value (255,255,0)
    - **yellowGreen** (Yellow Green Preset Color):  Specifies a color with RGB value (154,205,50)

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetColorVal) is located in §A.4.1. end note]

## 20.1.10.49 ST_PresetLineDashVal (预设线型/轮廓虚线)

=== "中文"

    !!! info "译注"

        pdf 文档有图片样例

    这个简单类型表示预设线条虚线样式。每种样式的描述都显示了该线条样式的示意图。每种样式还包含了一个精确的二进制表示，表示重复的虚线样式。每个1对应于与线宽相同长度的线段，而每个0对应于与线宽相同长度的空白(space)。
    
    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **dash**（短划线）：1111000
    - **dashDot**（短划点线）：11110001000
    - **dot**（点线）：1000
    - **lgDash**（长短划线）：11111111000
    - **lgDashDot**（长短划点线）：111111110001000
    - **lgDashDotDot**（长短划点点线）：1111111100010001000
    - **solid**（实线）：1
    - **sysDash**（系统短划线）：1110
    - **sysDashDot**（系统短划点线）：111010
    - **sysDashDotDot**（系统短划点点线）：11101010
    - **sysDot**（系统点线）：10
    
    [注意：这个简单类型内容模型（ST_PresetLineDashVal）的W3C XML Schema定义位于§A.4.1。末尾注释]

=== "英文"

    **ST_PresetLineDashVal (Preset Line Dash Value)**

    This simple type represents preset line dash values. The description for each style shows an illustration of the line style. Each style also contains a precise binary representation of the repeating dash style. Each 1 corresponds to a line segment of the same length as the line width, and each 0 corresponds to a space of the same length as the line width.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **dash** (Dash): 1111000
    - **dashDot** (Dash Dot): 11110001000
    - **dot** (Dot): 1000
    - **lgDash** (Large Dash): 11111111000
    - **lgDashDot** (Large Dash Dot): 111111110001000
    - **lgDashDotDot** (Large Dash Dot Dot): 1111111100010001000
    - **solid** (Solid): 1
    - **sysDash** (System Dash): 1110
    - **sysDashDot** (System Dash Dot): 111010
    - **sysDashDotDot** (System Dash Dot Dot): 11101010
    - **sysDot** (System Dot): 10
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetLineDashVal) is located in §A.4.1. end note]

    !!! info "译注"

        pdf 文档有图片样例

## 20.1.10.50 ST_PresetMaterialType (预设材质类型)

=== "中文"

    !!! info "译注"

        图片参看pdf原文.
    
    描述形状的表面外观。材质类型与光照特性结合，以创建形状的最终外观和感觉。可以组合在一起创建以下预设的一组材质属性包括：

    - 镜面颜色(Specular color) – 定义与材料关联的高光的颜色。
    - 镜面功率(Specular power) – 定义高光的大小和强度。较小的值提供较大但不太强烈的高光，而较大的值提供较小但更强烈的高光。
    - 漫反射颜色(Diffuse color) – 定义材料在直接受到光源照明的地方的感知颜色。一般来说，这里的默认颜色将基于形状的填充颜色。
    - 环境颜色(Ambient color) – 定义材料在没有直接受到光源照明的地方的感知颜色。一般来说，这里的默认颜色将基于形状的填充颜色。
    - 自发光颜色(Emissive color) – 定义由对象发出的光的颜色。
    - 漫反射菲涅耳效应(Diffuse Fresnel effect) – 这是一种在斜视角度上使材料类型的漫反射颜色变暗（趋向于黑色）或变亮（趋向于白色）的效果。正值使材料变得更亮，负值使材料变得更暗。
    - Alpha 菲涅耳效应(Alpha Fresnel effect) – 这是一种在斜视角度上使材料变得更不透明或更透明的效果。正值使材料变得更不透明，负值使材料变得更透明。

    在以下示例中，对于某些属性给出的确切值应被理解为相对值，以提供参考。这些值可能因用于渲染材料类型的技术而有所不同。以下属性用于定义下面示例图像中使用的形状：

    - 圆角矩形形状(Rounded rectangle shape)
    - 圆形斜角类型(Circle bevel type)
    - 三点光照系统类型(Three Point light rig type)
    - 由透视对比右侧预设定义的摄像机类型(Camera type defined by the perspectiveContrastingRightFacing preset)
    - 斜角宽度和高度均等于 190500(Bevel width and height each equal to 190500)

    此简单类型的内容是 W3C XML Schema 令牌数据类型的限制。

    此简单类型仅限于以下表中列出的值：

    **clear (Clear)**:

    :   The `clear` material type has the following characteristics:

        - Specular Color: light gray
        - Diffuse Color: shape fill color with 90% alpha
        - Ambient Color: shape fill color with 90% alpha
        - Emissive Color: black
        - Diffuse Fresnel value: -8
        - Alpha Fresnel value: 1
        
        [Example: Consider the following example of the `clear` material type: ![123](./imgs/aaa.png) end example]

    **dkEdge (Dark Edge) **:

    :   The `dkEdge` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 35
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: -2

        [Example: Consider the following example of the `dkEdge` material type: ![123](./imgs/aaa.png) end example]

    **flat (Flat)**:

    :   The `flat` material type has the following characteristics:

        - Specular Color: very light gray
        - Specular Power value: 50
        - Diffuse Color: black
        - Ambient Color: black
        - Emissive Color: shape fill color
        - Diffuse Fresnel value: -4

        [Example: Consider the following example of the `flat` material type: ![123](./imgs/aaa.png) end example]

    **legacyMatte (Legacy Matte)**:

    :   The `legacyMatte` material type has the following characteristics:

        - Specular Color: black
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: -4

        [Example: Consider the following example of the `legacyMatte` material type: ![123](./imgs/aaa.png) end example]

    **legacyMetal (Legacy Metal)**:

    :   The `legacyMetal` material type has the following characteristics:

        - Specular Color: shape fill color
        - Specular Power value: 32
        - Diffuse Color: shape fill color darkened by adding black
        - Ambient Color: shape fill color darkened by adding black
        - Emissive Color: black

        [Example: Consider the following example of the `legacyMetal` material type: ![123](./imgs/aaa.png) end example]

    **legacyPlastic (Legacy Plastic)**:

    :   The `legacyPlastic` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 32
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `legacyPlastic` material type: ![123](./imgs/aaa.png) end example]

    **legacyWireframe (Legacy Wireframe)**:

    :   The `legacyWireframe` material type has none of the associated material properties and is based on a wireframe interpretation of the shape.

        - Specular Color: white
        - Specular Power value: 32
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `legacyWireframe` material type: ![123](./imgs/aaa.png) end example]

    **matte (Matte) **:

    :   The `matte` material type has the following characteristics:

        - Specular Color: black
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `matte` material type: ![123](./imgs/aaa.png) end example]

    **metal (Metal)**:

    :   The `metal` material type has the following characteristics:

        - Specular Color: shape fill color plus white, which is brightened by 1.5 times the normal value
        - Specular Power value: 12
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: 4

        [Example: Consider the following example of the `metal` material type: ![123](./imgs/aaa.png) end example]

    **plastic (Plastic) **:

    :   The `plastic` material type has the following characteristics:

        - Specular Color: light gray
        - Specular Power value: 12
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `plastic` material type: ![123](./imgs/aaa.png) end example]

    **powder (Powder) **:

    :   The `powder` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 10
        - Diffuse Color: gray
        - Ambient Color: gray
        - Emissive Color: black
        - Diffuse Fresnel value: 2

        [Example: Consider the following example of the `powder` material type: ![123](./imgs/aaa.png) end example]

    **softEdge (Soft Edge) **:

    :   The `softEdge` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 35
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: 4
        - Alpha Fresnel value: -10

        [Example: Consider the following example of the `softEdge` material type: ![123](./imgs/aaa.png) end example]

    **softmetal (Soft Metal)**:

    :   The `softmetal` material type has the following characteristics:

        - Specular Color: shape fill color lightened with white by 50%
        - Specular Power value: 8
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `softmetal` material type: ![123](./imgs/aaa.png) end example]

    **translucentPowder (Translucent Powder)**:

    :   The `translucentPowder` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 10
        - Diffuse Color: shape fill color with 30% transparency
        - Ambient Color: shape fill color with 30% transparency
        - Emissive Color: black
        - Diffuse Fresnel value: 2
        - Alpha Fresnel value: -1

        [Example: Consider the following example of the `translucentPowder` material type: ![123](./imgs/aaa.png) end example]

    **warmMatte (Warm Matte) **:

    :   The `warmMatte` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 8
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `warmMatte` material type: ![123](./imgs/aaa.png) end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetMaterialType) is located in §A.4.1. end note]

=== "英文"

    **ST_PresetMaterialType (Preset Material Type)**

    Describes surface appearance of a shape. The material type combines with lighting characteristics to create the final look and feel of a shape. The set of material properties which can be combined together to create the presets below consist of the following characteristics:

    - Specular color – This defines the color of the highlight associated with the material.
    - Specular power – This defines the size and how intense the highlight is. Smaller values provide a larger, but less intense highlight, while larger values provide a smaller, but more intense highlight.
    - Diffuse color – This defines the perceived color of the material where an object is directly illuminated by a light source. Generally speaking, the default color here would be based on the shape fill color.
    - Ambient color – This defines the perceived color of the material where an object is not directly illuminated by a light source. Generally speaking, the default color here would be based on the shape fill color.
    - Emissive color – This defines the color of a light which is perceived to be given off by an object.
    - Diffuse Fresnel effect – This is an effect that either darkens (approaches black) or lightens (approaches white) the diffuse color of the material type at glancing angles. Positive values cause the material to become brighter, negative values cause the material to become darker.
    - Alpha Fresnel effect – This is an effect that either makes the material more opaque or more transparent at glancing angles. Positive values cause the material to become more opaque, negative values cause the material to become more transparent.
    
    In the following examples, the exact values given for certain properties should be understood to be relative values in order to provide a reference. These values could be different depending upon technologies used to render the material types. The following properties were used to define the shape used in the image examples below:
    
    - Rounded rectangle shape
    - Circle bevel type
    - Three Point light rig type
    - Camera type defined by the perspectiveContrastingRightFacing preset
    - Bevel width and height each equal to 190500
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **clear (Clear)**:

    :   The `clear` material type has the following characteristics:

        - Specular Color: light gray
        - Diffuse Color: shape fill color with 90% alpha
        - Ambient Color: shape fill color with 90% alpha
        - Emissive Color: black
        - Diffuse Fresnel value: -8
        - Alpha Fresnel value: 1
        
        [Example: Consider the following example of the `clear` material type: ![123](./imgs/aaa.png) end example]

    **dkEdge (Dark Edge) **:

    :   The `dkEdge` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 35
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: -2

        [Example: Consider the following example of the `dkEdge` material type: ![123](./imgs/aaa.png) end example]

    **flat (Flat)**:

    :   The `flat` material type has the following characteristics:

        - Specular Color: very light gray
        - Specular Power value: 50
        - Diffuse Color: black
        - Ambient Color: black
        - Emissive Color: shape fill color
        - Diffuse Fresnel value: -4

        [Example: Consider the following example of the `flat` material type: ![123](./imgs/aaa.png) end example]

    **legacyMatte (Legacy Matte)**:

    :   The `legacyMatte` material type has the following characteristics:

        - Specular Color: black
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: -4

        [Example: Consider the following example of the `legacyMatte` material type: ![123](./imgs/aaa.png) end example]

    **legacyMetal (Legacy Metal)**:

    :   The `legacyMetal` material type has the following characteristics:

        - Specular Color: shape fill color
        - Specular Power value: 32
        - Diffuse Color: shape fill color darkened by adding black
        - Ambient Color: shape fill color darkened by adding black
        - Emissive Color: black

        [Example: Consider the following example of the `legacyMetal` material type: ![123](./imgs/aaa.png) end example]

    **legacyPlastic (Legacy Plastic)**:

    :   The `legacyPlastic` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 32
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `legacyPlastic` material type: ![123](./imgs/aaa.png) end example]

    **legacyWireframe (Legacy Wireframe)**:

    :   The `legacyWireframe` material type has none of the associated material properties and is based on a wireframe interpretation of the shape.

        - Specular Color: white
        - Specular Power value: 32
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `legacyWireframe` material type: ![123](./imgs/aaa.png) end example]

    **matte (Matte) **:

    :   The `matte` material type has the following characteristics:

        - Specular Color: black
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `matte` material type: ![123](./imgs/aaa.png) end example]

    **metal (Metal)**:

    :   The `metal` material type has the following characteristics:

        - Specular Color: shape fill color plus white, which is brightened by 1.5 times the normal value
        - Specular Power value: 12
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: 4

        [Example: Consider the following example of the `metal` material type: ![123](./imgs/aaa.png) end example]

    **plastic (Plastic) **:

    :   The `plastic` material type has the following characteristics:

        - Specular Color: light gray
        - Specular Power value: 12
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `plastic` material type: ![123](./imgs/aaa.png) end example]

    **powder (Powder) **:

    :   The `powder` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 10
        - Diffuse Color: gray
        - Ambient Color: gray
        - Emissive Color: black
        - Diffuse Fresnel value: 2

        [Example: Consider the following example of the `powder` material type: ![123](./imgs/aaa.png) end example]

    **softEdge (Soft Edge) **:

    :   The `softEdge` material type has the following characteristics:

        - Specular Color: white
        - Specular Power value: 35
        - Ambient Color: shape fill color
        - Emissive Color: black
        - Diffuse Fresnel value: 4
        - Alpha Fresnel value: -10

        [Example: Consider the following example of the `softEdge` material type: ![123](./imgs/aaa.png) end example]

    **softmetal (Soft Metal)**:

    :   The `softmetal` material type has the following characteristics:

        - Specular Color: shape fill color lightened with white by 50%
        - Specular Power value: 8
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `softmetal` material type: ![123](./imgs/aaa.png) end example]

    **translucentPowder (Translucent Powder)**:

    :   The `translucentPowder` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 10
        - Diffuse Color: shape fill color with 30% transparency
        - Ambient Color: shape fill color with 30% transparency
        - Emissive Color: black
        - Diffuse Fresnel value: 2
        - Alpha Fresnel value: -1

        [Example: Consider the following example of the `translucentPowder` material type: ![123](./imgs/aaa.png) end example]

    **warmMatte (Warm Matte) **:

    :   The `warmMatte` material type has the following characteristics:

        - Specular Color: dark gray
        - Specular Power value: 8
        - Ambient Color: shape fill color
        - Emissive Color: black

        [Example: Consider the following example of the `warmMatte` material type: ![123](./imgs/aaa.png) end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetMaterialType) is located in §A.4.1. end note]

    !!! info "译注"

        图片参看pdf原文.

## 20.1.10.51 ST_PresetPatternVal (预设图案值)

=== "中文"

    !!! info "译注"

        pdf 文档有图片样例

    预设图案填充类型表示一种预设的图案填充类型。每个值的描述都包含了该填充类型的示例图。

    [注：这些预设对应于 Microsoft .NET Framework 中的 HatchStyle 枚举的成员。有关此类型的参考，请参阅 http://msdn2.microsoft.com/enus/library/system.drawing.drawing2d.hatchstyle.aspx。结束注释]
    
    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。
    
    这个简单类型仅限于以下表中列出的值：

    **Enumeration**

    - **cross** (十字 / Cross) : ![123](./imgs/aaa.png)
    - **dashDnDiag** (向下虚线对角线 / Dashed Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dashHorz** (水平虚线 / Dashed Horizontal) : ![123](./imgs/aaa.png)
    - **dashUpDiag** (向上虚线对角线 / Dashed Upward DIagonal) : ![123](./imgs/aaa.png)
    - **dashVert** (垂直虚线 / Dashed Vertical) : ![123](./imgs/aaa.png)
    - **diagBrick** (对角砖 / Diagonal Brick) : ![123](./imgs/aaa.png)
    - **diagCross** (对角十字 / Diagonal Cross) : ![123](./imgs/aaa.png)
    - **divot** (Divot) : ![123](./imgs/aaa.png)
    - **dkDnDiag** (Dark Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dkHorz** (Dark Horizontal) : ![123](./imgs/aaa.png)
    - **dkUpDiag** (Dark Upward Diagonal) : ![123](./imgs/aaa.png)
    - **dkVert** (Dark Vertical) : ![123](./imgs/aaa.png)
    - **dnDiag** (Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dotDmnd** (Dotted Diamond) : ![123](./imgs/aaa.png)
    - **dotGrid** (Dotted Grid) : ![123](./imgs/aaa.png)
    - **horz** (Horizontal) : ![123](./imgs/aaa.png)
    - **horzBrick** (Horizontal Brick) : ![123](./imgs/aaa.png)
    - **lgCheck** (Large Checker Board) : ![123](./imgs/aaa.png)
    - **lgConfetti** (Large Confetti) : ![123](./imgs/aaa.png)
    - **lgGrid** (Large Grid) : ![123](./imgs/aaa.png)
    - **ltDnDiag** (Light Downward Diagonal) : ![123](./imgs/aaa.png)
    - **ltHorz** (Light Horizontal) : ![123](./imgs/aaa.png)
    - **ltUpDiag** (Light Upward Diagonal) : ![123](./imgs/aaa.png)
    - **ltVert** (Light Vertical) : ![123](./imgs/aaa.png)
    - **narHorz** (Narrow Horizontal) : ![123](./imgs/aaa.png)
    - **narVert** (Narrow Vertical) : ![123](./imgs/aaa.png)
    - **openDmnd** (Open Diamond) : ![123](./imgs/aaa.png)
    - **pct10** (10%) ： ![123](./imgs/aaa.png)
    - **pct20** (20%) ： ![123](./imgs/aaa.png)
    - **pct25** (25%) ： ![123](./imgs/aaa.png)
    - **pct30** (30%) ： ![123](./imgs/aaa.png)
    - **pct40** (40%) ： ![123](./imgs/aaa.png)
    - **pct5** (5%) : ![123](./imgs/aaa.png)
    - **pct50** (50%) : ![123](./imgs/aaa.png)
    - **pct60** (60%) : ![123](./imgs/aaa.png)
    - **pct70** (70%) : ![123](./imgs/aaa.png)
    - **pct75** (75%) : ![123](./imgs/aaa.png)
    - **pct80** (80%) : ![123](./imgs/aaa.png)
    - **pct90** (90%) : ![123](./imgs/aaa.png)
    - **plaid** (Plaid) : ![123](./imgs/aaa.png)
    - **shingle** (Shingle) : ![123](./imgs/aaa.png)
    - **smCheck** (Small Checker Board) : ![123](./imgs/aaa.png)
    - **smConfetti** (Small Confetti) : ![123](./imgs/aaa.png)
    - **smGrid** (Small Grid) : ![123](./imgs/aaa.png)
    - **solidDmnd** (Solid Diamond) : ![123](./imgs/aaa.png)
    - **sphere** (Sphere) : ![123](./imgs/aaa.png)
    - **trellis** (Trellis) : ![123](./imgs/aaa.png)
    - **upDiag** (Upward Diagonal) : ![123](./imgs/aaa.png)
    - **vert** (Vertical) : ![123](./imgs/aaa.png)
    - **wave** (Wave) : ![123](./imgs/aaa.png)
    - **wdDnDiag** (Wide Downward Diagonal) : ![123](./imgs/aaa.png)
    - **wdUpDiag** (Wide Upward Diagonal) : ![123](./imgs/aaa.png)
    - **weave** (Weave) : ![123](./imgs/aaa.png)
    - **zigZag** (Zig Zag) : ![123](./imgs/aaa.png)

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetPatternVal) is located in §A.4.1. end note]

=== "英文"

    **ST_PresetPatternVal (Preset Pattern Value)**

    !!! info "译注"

        pdf 文档有图片样例

    This simple type indicates a preset type of pattern fill. The description of each value contains an illustration of the fill type.

    [Note: These presets correspond to members of the HatchStyle enumeration in the Microsoft .NET Framework. A reference for this type can be found at http://msdn2.microsoft.com/enus/library/system.drawing.drawing2d.hatchstyle.aspx. end note]

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    - **cross** (Cross) : ![123](./imgs/aaa.png)
    - **dashDnDiag** (Dashed Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dashHorz** (Dashed Horizontal) : ![123](./imgs/aaa.png)
    - **dashUpDiag** (Dashed Upward DIagonal) : ![123](./imgs/aaa.png)
    - **dashVert** (Dashed Vertical) : ![123](./imgs/aaa.png)
    - **diagBrick** (Diagonal Brick) : ![123](./imgs/aaa.png)
    - **diagCross** (Diagonal Cross) : ![123](./imgs/aaa.png)
    - **divot** (Divot) : ![123](./imgs/aaa.png)
    - **dkDnDiag** (Dark Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dkHorz** (Dark Horizontal) : ![123](./imgs/aaa.png)
    - **dkUpDiag** (Dark Upward Diagonal) : ![123](./imgs/aaa.png)
    - **dkVert** (Dark Vertical) : ![123](./imgs/aaa.png)
    - **dnDiag** (Downward Diagonal) : ![123](./imgs/aaa.png)
    - **dotDmnd** (Dotted Diamond) : ![123](./imgs/aaa.png)
    - **dotGrid** (Dotted Grid) : ![123](./imgs/aaa.png)
    - **horz** (Horizontal) : ![123](./imgs/aaa.png)
    - **horzBrick** (Horizontal Brick) : ![123](./imgs/aaa.png)
    - **lgCheck** (Large Checker Board) : ![123](./imgs/aaa.png)
    - **lgConfetti** (Large Confetti) : ![123](./imgs/aaa.png)
    - **lgGrid** (Large Grid) : ![123](./imgs/aaa.png)
    - **ltDnDiag** (Light Downward Diagonal) : ![123](./imgs/aaa.png)
    - **ltHorz** (Light Horizontal) : ![123](./imgs/aaa.png)
    - **ltUpDiag** (Light Upward Diagonal) : ![123](./imgs/aaa.png)
    - **ltVert** (Light Vertical) : ![123](./imgs/aaa.png)
    - **narHorz** (Narrow Horizontal) : ![123](./imgs/aaa.png)
    - **narVert** (Narrow Vertical) : ![123](./imgs/aaa.png)
    - **openDmnd** (Open Diamond) : ![123](./imgs/aaa.png)
    - **pct10** (10%) ： ![123](./imgs/aaa.png)
    - **pct20** (20%) ： ![123](./imgs/aaa.png)
    - **pct25** (25%) ： ![123](./imgs/aaa.png)
    - **pct30** (30%) ： ![123](./imgs/aaa.png)
    - **pct40** (40%) ： ![123](./imgs/aaa.png)
    - **pct5** (5%) : ![123](./imgs/aaa.png)
    - **pct50** (50%) : ![123](./imgs/aaa.png)
    - **pct60** (60%) : ![123](./imgs/aaa.png)
    - **pct70** (70%) : ![123](./imgs/aaa.png)
    - **pct75** (75%) : ![123](./imgs/aaa.png)
    - **pct80** (80%) : ![123](./imgs/aaa.png)
    - **pct90** (90%) : ![123](./imgs/aaa.png)
    - **plaid** (Plaid) : ![123](./imgs/aaa.png)
    - **shingle** (Shingle) : ![123](./imgs/aaa.png)
    - **smCheck** (Small Checker Board) : ![123](./imgs/aaa.png)
    - **smConfetti** (Small Confetti) : ![123](./imgs/aaa.png)
    - **smGrid** (Small Grid) : ![123](./imgs/aaa.png)
    - **solidDmnd** (Solid Diamond) : ![123](./imgs/aaa.png)
    - **sphere** (Sphere) : ![123](./imgs/aaa.png)
    - **trellis** (Trellis) : ![123](./imgs/aaa.png)
    - **upDiag** (Upward Diagonal) : ![123](./imgs/aaa.png)
    - **vert** (Vertical) : ![123](./imgs/aaa.png)
    - **wave** (Wave) : ![123](./imgs/aaa.png)
    - **wdDnDiag** (Wide Downward Diagonal) : ![123](./imgs/aaa.png)
    - **wdUpDiag** (Wide Upward Diagonal) : ![123](./imgs/aaa.png)
    - **weave** (Weave) : ![123](./imgs/aaa.png)
    - **zigZag** (Zig Zag) : ![123](./imgs/aaa.png)

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetPatternVal) is located in §A.4.1. end note]

## 20.1.10.52 ST_PresetShadowVal (预设阴影类型)

=== "中文"

    !!! info "译注"

        pdf 文档有图片样例

    这个简单类型表示 20 种预设阴影类型之一。每个枚举值的描述都说明了该值表示的阴影类型。每个描述都包含预设的外部阴影效果的参数，以及所有 prstShdw 效果共有的属性。

    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。
    
    这个简单类型仅限于以下表中列出的值：

    **shdw1 (左上角阴影 / Top Left Drop Shadow)**
    
    :   ![123](./imgs/aaa.png)
        - align = "br"
        - sx = 125%
        - sy = 125%

    **shdw11 (左后长透视阴影 / Back Left Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = 50%

    **shdw12 (右后长透视阴影 / Back Right Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = 50%

    **shdw13 (左上双阴影 / Top Left Double Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        相当于两个外阴影效果。

        Shadow 1: 没有指定其他属性。
        
        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dist = 2 * shadow 1's distance

    **shdw14 (右下小阴影 / Bottom Right Small Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        没有指定其他属性。

    **shdw15 (左前长透视阴影 / Front Left Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = -50%

    **shdw16 (右前长透视阴影 / Front Right Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = -50%

    **shdw17 (3D外盒阴影 / 3D Outer Box Shadow)**

    :   ![123](./imgs/aaa.png)
        
        Equivalent to two outer shadow effects.
            
        Shadow 1: 没有指定其他属性。

        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dir = shadow 1's direction + 180°

    **shdw18 (3D 内盒阴影 / 3D Inner Box Shadow)**

    :   ![123](./imgs/aaa.png)
        
        Equivalent to two outer shadow effects.
            
        Shadow 1: 没有指定其他属性。

        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dir = shadow 1's direction + 180°

    **shdw19 (后中心透视阴影 / Back Center Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - sy = 50°

    **shdw2 (右上角投影 / Top Right Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        没有指定其他属性。

    **shdw20 (前底阴影 / Front Bottom Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - sy = -100°

    **shdw3 (左后透视阴影 / Back Left Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - ky = 40.89°
        - sy = 50%

    **shdw4 (后右透视阴影 / Back Right Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = 50%

    **shdw5 (左下阴影 / Bottom Left Drop Shadow)**

    :   ![123](./imgs/aaa.png)

        没有指定其他属性。

    **shdw6 (右下阴影 / Bottom Right Drop Shadow)**

    :   ![123](./imgs/aaa.png)
    
        没有指定其他属性。

    **shdw7 (左前透视阴影 / Front Left Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = -50%

    **shdw8 (右前透视阴影 / Front Right Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = -50%

    **shdw9 (左上小阴影 / Top Left Small Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "tl"
        - kx = 75%
        - sy = 75%

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetShadowVal) is located in §A.4.1. end note]

=== "英文"

    **ST_PresetShadowVal (Preset Shadow Type)**

    !!! info "译注"

        pdf 文档有图片样例

    This simple type indicates one of 20 preset shadow types. Each enumeration value description illustrates the type of shadow represented by the value. Each description contains the parameters to the outer shadow effect represented by the preset, in addition to those attributes common to all prstShdw effects.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **shdw1 (Top Left Drop Shadow)**
    
    :   ![123](./imgs/aaa.png)
        - align = "br"
        - sx = 125%
        - sy = 125%

    **shdw11 (Back Left Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = 50%

    **shdw12 (Back Right Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = 50%

    **shdw13 (Top Left Double Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        Equivalent to two outer shadow effects.

        Shadow 1: No additional attributes specified.
        
        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dist = 2 * shadow 1's distance

    **shdw14 (Bottom Right Small Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        No additional attributes specified.

    **shdw15 (Front Left Long Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = -50%

    **shdw16 (Front Right LongPerspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = -50%

    **shdw17 (3D Outer Box Shadow)**

    :   ![123](./imgs/aaa.png)
        
        Equivalent to two outer shadow effects.
            
        Shadow 1: No additional attributes specified.

        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dir = shadow 1's direction + 180°

    **shdw18 (3D Inner Box Shadow)**

    :   ![123](./imgs/aaa.png)
        
        Equivalent to two outer shadow effects.
            
        Shadow 1: No additional attributes specified.

        Shadow 2: color = min(1, shadow 1's color (0 <= r, g, b <= 1) + 102/255), per r, g, b component dir = shadow 1's direction + 180°

    **shdw19 (Back Center Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - sy = 50°

    **shdw2 (Top Right Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        
        No additional attributes specified.

    **shdw20 (Front Bottom Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - sy = -100°

    **shdw3 (Back Left Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - ky = 40.89°
        - sy = 50%

    **shdw4 (Back Right Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = 50%

    **shdw5 (Bottom Left Drop Shadow)**

    :   ![123](./imgs/aaa.png)

        No additional attributes specified.

    **shdw6 (Bottom Right Drop Shadow)**

    :   ![123](./imgs/aaa.png)
    
        No additional attributes specified.

    **shdw7 (Front Left Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = 40.89°
        - sy = -50%

    **shdw8 (Front Right Perspective Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "b"
        - kx = -40.89°
        - sy = -50%

    **shdw9 (Top Left Small Drop Shadow)**

    :   ![123](./imgs/aaa.png)
        - align = "tl"
        - kx = 75%
        - sy = 75%

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PresetShadowVal) is located in §A.4.1. end note]

## 20.1.10.53 ST_RectAlignment (矩形对齐)

=== "中文"

    这个简单类型描述了如何相对放置两个矩形。

    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。

    这个简单类型仅限于以下表中列出的值：

    - **b**（矩形对齐枚举（底部）） - 底部
    - **bl**（矩形对齐枚举（左下）） - 左下
    - **br**（矩形对齐枚举（右下）） - 右下
    - **ctr**（矩形对齐枚举（中心）） - 中心
    - **l**（矩形对齐枚举（左）） - 左
    - **r**（矩形对齐枚举（右）） - 右
    - **t**（矩形对齐枚举（上）） - 上
    - **tl**（矩形对齐枚举（左上）） - 左上
    - **tr**（矩形对齐枚举（右上）） - 右上

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_RectAlignment) is located in §A.4.1. end note]

=== "英文"

    **ST_RectAlignment (Rectangle Alignments)**

    This simple type describes how to position two rectangles relative to each other.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    - **b** (Rectangle Alignment Enum ( Bottom )) - Bottom
    - **bl** (Rectangle Alignment Enum ( Bottom Left )) - Bottom Left
    - **br** (Rectangle Alignment Enum ( Bottom Right )) - Bottom Right
    - **ctr** (Rectangle Alignment Enum ( Center )) - Center
    - **l** (Rectangle Alignment Enum ( Left )) - Left
    - **r** (Rectangle Alignment Enum ( Right )) - Right
    - **t** (Rectangle Alignment Enum ( Top )) - Top
    - **tl** (Rectangle Alignment Enum ( Top Left )) - Top Left
    - **tr** (Rectangle Alignment Enum ( Top Right )) - Top Right

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_RectAlignment) is located in §A.4.1. end note]

## 20.1.10.54 ST_SchemeColorVal (配色方案颜色值)

=== "中文"

    这个简单类型表示一个配色方案的颜色值。

    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。
    
    这个简单类型仅限于以下表中列出的值：
    
    - **accent1**（强调颜色 1）：额外的配色方案颜色 1
    - **accent2**（强调颜色 2）：额外的配色方案颜色 2
    - **accent3**（强调颜色 3）：额外的配色方案颜色 3
    - **accent4**（强调颜色 4）：额外的配色方案颜色 4
    - **accent5**（强调颜色 5）：额外的配色方案颜色 5
    - **accent6**（强调颜色 6）：额外的配色方案颜色 6
    - **bg1**（背景颜色 1）：语义背景颜色
    - **bg2**（背景颜色 2）：语义附加背景颜色
    - **dk1**（深色 1）：主深色 1
    - **dk2**（深色 2）：主深色 2
    - **folHlink**（已访问的超链接颜色）：已访问的超链接颜色
    - **hlink**（超链接颜色）：常规超链接颜色
    - **lt1**（浅色 1）：主浅色 1
    - **lt2**（浅色 2）：主浅色 2
    - **phClr**（样式颜色）：在主题定义中使用的一种颜色，表示使用样式的颜色。
    - **tx1**（文本颜色 1）：语义文本颜色
    - **tx2**（文本颜色 2）：语义附加文本颜色

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SchemeColorVal) is located in §A.4.1. end note]

=== "英文"

    **ST_SchemeColorVal (Scheme Color)**

    This simple type represents a scheme color value.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **accent1** (Accent Color 1): Extra scheme color 1
    - **accent2** (Accent Color 2): Extra scheme color 2
    - **accent3** (Accent Color 3): Extra scheme color 3
    - **accent4** (Accent Color 4): Extra scheme color 4
    - **accent5** (Accent Color 5): Extra scheme color 5
    - **accent6** (Accent Color 6): Extra scheme color 6
    - **bg1** (Background Color 1): Semantic background color
    - **bg2** (Background Color 2): Semantic additional background color
    - **dk1** (Dark Color 1): Main dark color 1
    - **dk2** (Dark Color 2): Main dark color 2
    - **folHlink** (Followed Hyperlink Color): Followed Hyperlink Color
    - **hlink** (Hyperlink Color): Regular Hyperlink Color
    - **lt1** (Light Color 1): Main Light Color 1
    - **lt2** (Light Color 2): Main Light Color 2
    - **phClr** (Style Color): A color used in theme definitions which means to use the color of the style.
    - **tx1** (Text Color 1): Semantic text color
    - **tx2** (Text Color 2): Semantic additional text color

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SchemeColorVal) is located in §A.4.1. end note]

## 20.1.10.55 ST_ShapeID (形状ID)

=== "中文"

    指定用于传统形状标识目的的形状 ID。
    
    这个简单类型的内容是对 W3C XML Schema 令牌数据类型的限制。
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ShapeID) is located in §A.4.1.
    end note]

=== "英文"

    **ST_ShapeID (Shape ID)**
    
    Specifies the shape ID for legacy shape identification purposes.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ShapeID) is located in §A.4.1.
    end note]

## 20.1.10.56 ST_ShapeType (预设形状类型)

=== "中文"

    !!! info "译注"

        pdf 文档有图片样例

    这个简单类型指定了要用于形状的预设形状几何。使用此简单类型的枚举，可以自动生成形状，而无需指定自定义几何形状。对于列出的每个枚举，还有相应的 DrawingML 代码，该代码将用于构造此形状，如果它是一个自定义几何形状的话。在这些预设形状的构造代码中，生成应用程序应始终保持用于计算的预定义引导。所需的引导应具有以下值。公式语法组件在 gd 元素的 fmla 属性中定义（§20.1.9.11）。
    
    **3/4 圆 ('3cd4') - 常量值为 "16200000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 270 度。
    
    **3/8 圆 ('3cd8') - 常量值为 "8100000.0"**

    :   此处的单位是 60,000 分之一度。这相当于 135 度。
    
    **5/8 圆 ('5cd8') - 常量值为 "13500000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 225 度。
    
    **7/8 圆 ('7cd8') - 常量值为 "18900000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 315 度。
    
    **形状底边 ('b') - 常量值为 "h"**
    
    :   这是形状的底边，由于形状的顶边被认为是0点，底边因此是形状的高度。
    
    **1/2 圆 ('cd2') - 常量值为 "10800000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 180 度。
    
    **1/4 圆 ('cd4') - 常量值为 "5400000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 90 度。
    
    **1/8 圆 ('cd8') - 常量值为 "2700000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 45 度。
    
    **形状高度 ('h')**
    
    :   这是形状属性中定义的形状的可变高度。此值来自 `<spPr>` 元素中列出的形状变换。
    
    **水平中心 ('hc') - 计算值为 "*/ w 1.0 2.0"**

    :   这是形状的水平中心，即宽度除以2。
    
    **形状高度的1/2 ('hd2') - 计算值为 "*/ h 1.0 2.0"**
    
    :   这是形状高度的1/2。
    
    **形状高度的1/3 ('hd3') - 计算值为 "*/ h 1.0 3.0"**
    
    :   这是形状高度的1/3。
    
    **形状高度的1/4 ('hd4') - 计算值为 "*/ h 1.0 4.0"**
    
    :   这是形状高度的1/4。
    
    **形状高度的1/5 ('hd5') - 计算值为 "*/ h 1.0 5.0"**
    
    :   这是形状高度的1/5。
    
    **形状高度的1/6 ('hd6') - 计算值为 "*/ h 1.0 6.0"**
    
    :   这是形状高度的1/6。
    
    **形状高度的1/8 ('hd8') - 计算值为 "*/ h 1.0 8.0"**
    
    :   这是形状高度的1/8。
    
    **形状左边 ('l') - 常量值为 "0"**
    
    :   这是形状的左边缘，形状的左边缘被认为是水平0点。
    
    **形状最长边 ('ls') - 计算值为 "max w h"**
    
    :   这是形状的最长边。该值是宽度或高度，取决于哪个更大。
    
    **形状右边 ('r') - 常量值为 "w"**
    
    :   这是形状的右边缘，由于形状的左边缘被认为是0点，右边缘因此是形状的宽度。
    
    **形状的最短边 ('ss') - 计算值为 "min w h"**

    :   这是形状的最短边。该值是宽度或高度，取决于哪个更小。
    
    **形状最短边的1/2 ('ssd2') - 计算值为 "*/ ss 1.0 2.0"**
    
    :   这是形状最短边的1/2。
    
    **形状最短边的1/4 ('ssd4') - 计算值为 "*/ ss 1.0 4.0"**
    
    :   这是形状最短边的1/4。
    
    **形状最短边的1/6 ('ssd6') - 计算值为 "*/ ss 1.0 6.0"**
    
    :   这是形状最短边的1/6。
    
    **形状最短边的1/8 ('ssd8') - 计算值为 "*/ ss 1.0 8.0"**
    
    :   这是形状最短边的1/8。
    
    **形状最短边的1/16 ('ssd16') - 计算值为 "*/ ss 1.0 16.0"**
    
    :   这是形状最短边的1/16。
    
    **形状最短边的1/32 ('ssd32') - 计算值为 "*/ ss 1.0 32.0"**
    
    :   这是形状最短边的1/32。
    
    **形状上边 ('t') - 常量值为 "0"**
    
    :   这是形状的上边缘，形状的上边缘被认为是垂直0点。
    
    **形状的垂直中心 ('vc') - 计算值为 "*/ h 1.0 2.0"**
    
    :   这是形状的垂直中心，即高度除以2。
    
    **形状宽度 ('w')**
    
    :   这是形状的可变宽度，定义在形状属性中。此值来自`<spPr>`元素中列出的形状变换。

    **形状宽度的1/2 ('wd2') - 计算值为 "*/ w 1.0 2.0"**

    :   这是形状宽度的1/2。
    
    **形状宽度的1/3 ('wd3') - 计算值为 "*/ w 1.0 3.0"**
    
    :   这是形状宽度的1/3。
    
    **形状宽度的1/4 ('wd4') - 计算值为 "*/ w 1.0 4.0"**
    
    :   这是形状宽度的1/4。
    
    **形状宽度的1/5 ('wd5') - 计算值为 "*/ w 1.0 5.0"**
    
    :   这是形状宽度的1/5。
    
    **形状宽度的1/6 ('wd6') - 计算值为 "*/ w 1.0 6.0"**
    
    :   这是形状宽度的1/6。
    
    **形状宽度的1/8 ('wd8') - 计算值为 "*/ w 1.0 8.0"**
    
    :   这是形状宽度的1/8。
    
    **形状宽度的1/10 ('wd10') - 计算值为 "*/ w 1.0 10.0"**
    
    :   这是形状宽度的1/10。
    
    此简单类型的内容受到W3C XML Schema令牌数据类型的限制。
    
    此简单类型限制为以下表中列出的值：

    ??? abstract "Enumeration"

        **accentBorderCallout1 (带边框和强调形状的标注 1 / Callout 1 with Border and Accent Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
            
            [注意：可用于生成此预设形状定义的DrawingML示例包含在附件D的预设形状几何电子附录中的accentBorderCallout1元素中。该标记中使用的常量是上述更详细描述的指南。结束注意]

            ![123](./imgs/aaa.png)

        **accentBorderCallout2 (带边框和强调形状的标注 2 / Callout 2 with Border and Accent Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentBorderCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentBorderCallout3 (带边框和强调形状的标注 3 / Callout 3 with Border and Accent Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentBorderCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout1 (标注 1 形状 / Callout 1 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout2 (标注 2 形状 / Callout 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout3 (标注 3 形状 / Callout 3 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBackPrevious (后退或上一个按钮形状 / Back or Previous Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBackPrevious element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBeginning (开始按钮形状 / Beginning Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBeginning element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBlank (空白按钮形状 / Blank Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBlank element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonDocument (文档按钮形状 / Document Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonDocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonEnd (结束按钮形状 / End Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonEnd element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonForwardNext (前进或下一个按钮形状 / Forward or Next Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonForwardNext element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonHelp (Help Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonHelp element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonHome (Home Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonHome element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonInformation (Information Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonInformation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonMovie (Movie Button Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonMovie element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonReturn (Return Button Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonReturn element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonSound (Sound Button Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonSound element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **arc (Curved Arc Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the arc element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentArrow (Bent Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector2 (Bent Connector 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector3 (Bent Connector 3 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector4 (Bent Connector 4 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector5 (Bent Connector 5 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentUpArrow (Bent Up Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bevel (Bevel Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bevel element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **blockArc (Block Arc Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the blockArc element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout1 (Callout 1 with Border Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout2 (Callout 2 with Border Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout3 (Callout 3 with Border Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bracePair (Brace Pair Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bracePair element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bracketPair (Bracket Pair Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bracketPair element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout1 (Callout 1 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout2 (Callout 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout3 (Callout 3 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **can (Can Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the can element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartPlus (Chart Plus Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartPlus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartStar (Chart Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartStar element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartX (Chart X Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartX element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chevron (Chevron Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chevron element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chord (Chord Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chord element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **circularArrow (Circular Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the circularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cloud (Cloud Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cloud element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cloudCallout (Callout Cloud Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cloudCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **corner (Corner Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the corner element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cornerTabs (Corner Tabs Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cornerTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cube (Cube Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cube element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector2 (Curved Connector 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector3 (Curved Connector 3 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector4 (Curved Connector 4 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector5 (Curved Connector 5 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedDownArrow (Curved Down Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedDownArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedLeftArrow (Curved Left Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedLeftArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedRightArrow (Curved Right Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedUpArrow (Curved Up Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **decagon (Decagon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the decagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **diagStripe (Diagonal Stripe Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the diagStripe element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **diamond (Diamond Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the diamond element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **dodecagon (Dodecagon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the dodecagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **donut (Donut Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the donut element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **doubleWave (Double Wave Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the doubleWave element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **downArrow (Down Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the downArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **downArrowCallout (Callout Down Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the downArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipse (Ellipse Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipse element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipseRibbon (Ellipse Ribbon Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipseRibbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipseRibbon2 (Ellipse Ribbon 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipseRibbon2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartAlternateProcess (Alternate Process Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartAlternateProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartCollate (Collate Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartCollate element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartConnector (Connector Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartConnector element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDecision (Decision Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDecision element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDelay (Delay Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDelay element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDisplay (Display Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDisplay (Display Flow Shape) element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDocument (Document Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartExtract (Extract Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartExtract element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartInputOutput (Input Output Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartInputOutput element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartInternalStorage (Internal Storage Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartInternalStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticDisk (Magnetic Disk Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticDisk element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticDrum (Magnetic Drum Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticDrum element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticTape (Magnetic Tape Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticTape element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartManualInput (Manual Input Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartManualInput element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartManualOperation (Manual Operation Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartManualOperation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMerge (Merge Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMerge element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMultidocument (Multi-Document Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMultidocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOfflineStorage (Offline Storage Flow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOfflineStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOffpageConnector (Off-Page Connector Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOffpageConnector element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOnlineStorage (Online Storage Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOnlineStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOr (Or Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOr element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPredefinedProcess (Predefined Process Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPredefinedProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPreparation (Preparation Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPreparation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartProcess (Process Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPunchedCard (Punched Card Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPunchedCard element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPunchedTape (Punched Tape Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPunchedTape element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartSort (Sort Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartSort element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartSummingJunction (Summing Junction Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartSummingJunction element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartTerminator (Terminator Flow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartTerminator element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **foldedCorner (Folded Corner Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the foldedCorner element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **frame (Frame Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the frame element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **funnel (Funnel Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the funnel element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **gear6 (Gear 6 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the gear6 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **gear9 (Gear 9 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the gear9 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **halfFrame (Half Frame Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the halfFrame element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **heart (Heart Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the heart element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **heptagon (Heptagon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the heptagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **hexagon (Hexagon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the hexagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **homePlate (Home Plate Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the homePlate element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **horizontalScroll (Horizontal Scroll Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the horizontalScroll element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **irregularSeal1 (Irregular Seal 1 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the irregularSeal1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **irregularSeal2 (Irregular Seal 2 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the irregularSeal2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftArrow (Left Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftArrowCallout (Callout Left Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftBrace (Left Brace Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftBrace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftBracket (Left Bracket Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftBracket element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftCircularArrow (Left Circular Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftCircularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightArrow (Left Right Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightArrowCallout (Callout Left Right Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightCircularArrow (Left Right Circular Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightCircularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightRibbon (Left Right Ribbon Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightRibbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightUpArrow (Left Right Up Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftUpArrow (Left Up Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **lightningBolt (Lightning Bolt Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the lightningBolt element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **line (Line Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the line element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **lineInv (Line Inverse Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the lineInv element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathDivide (Divide Math Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathDivide element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathEqual (Equal Math Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathEqual element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathMinus (Minus Math Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathMinus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathMultiply (Multiply Math Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathMultiply element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathNotEqual (Not Equal Math Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathNotEqual element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathPlus (Plus Math Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathPlus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **moon (Moon Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the moon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **nonIsoscelesTrapezoid (Non-Isosceles Trapezoid Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the nonIsoscelesTrapezoid element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **notchedRightArrow (Notched Right Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the notchedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **octagon (Octagon Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the octagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **parallelogram (Parallelogram Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the parallelogram element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pentagon (Pentagon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pentagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pie (Pie Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pie element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pieWedge (Pie Wedge Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pieWedge element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plaque (Plaque Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plaque element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plaqueTabs (Plaque Tabs Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plaqueTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plus (Plus Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **quadArrow (Quad-Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the quadArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **quadArrowCallout (Callout Quad-Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the quadArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rect (Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ribbon (Ribbon Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ribbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ribbon2 (Ribbon 2 Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ribbon2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightArrow (Right Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightArrowCallout (Callout Right Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightBrace (Right Brace Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightBrace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightBracket (Right Bracket Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightBracket element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round1Rect (One Round Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round1Rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round2DiagRect (Two Diagonal Round Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round2DiagRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round2SameRect (Two Same-side Round Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round2SameRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **roundRect (Round Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the roundRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rtTriangle (Right Triangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rtTriangle element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **smileyFace (Smiley Face Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the smileyFace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip1Rect (One Snip Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip1Rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip2DiagRect (Two Diagonal Snip Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip2DiagRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip2SameRect (Two Same-side Snip Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip2SameRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snipRoundRect (One Snip One Round Corner Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snipRoundRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **squareTabs (Square Tabs Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the squareTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star10 (Ten Pointed Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star10 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star12 (Twelve Pointed Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star12 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star16 (Sixteen Pointed Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star16 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star24 (Twenty Four Pointed Star Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star24 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star32 (Thirty Two Pointed Star Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star32 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star4 (Four Pointed Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star5 (Five Pointed Star Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star6 (Six Pointed Star Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star6 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star7 (Seven Pointed Star Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star7 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star8 (Eight Pointed Star Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star8 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **straightConnector1 (Straight Connector 1 Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the straightConnector1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **stripedRightArrow (Striped Right Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the stripedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **sun (Sun Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the sun element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **swooshArrow (Swoosh Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the swooshArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **teardrop (Teardrop Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the teardrop element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **trapezoid (Trapezoid Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the trapezoid element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **triangle (Triangle Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the triangle element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upArrow (Up Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upArrowCallout (Callout Up Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upDownArrow (Up Down Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upDownArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upDownArrowCallout (Callout Up Down Arrow Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upDownArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **uturnArrow (U-Turn Arrow Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the uturnArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **verticalScroll (Vertical Scroll Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the verticalScroll element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wave (Wave Shape) **

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wave element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeEllipseCallout (Callout Wedge Ellipse Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeEllipseCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeRectCallout (Callout Wedge Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeRectCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeRoundRectCallout (Callout Wedge Round Rectangle Shape)**

        :   指定一个预设的形状几何。此几何应设计为与下方规范图像相匹配。
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeRoundRectCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        [Note: The W3C XML Schema definition of this simple type’s content model (ST_ShapeType) is located in §A.4.1. end note]

=== "英文"

    **ST_ShapeType (Preset Shape Types)**

    !!! info "译注"

        pdf 文档有图片样例

    This simple type specifies the preset shape geometry that is to be used for a shape. An enumeration of this simple type is used so that a custom geometry does not have to be specified but instead can be constructed automatically by the generating application. For each enumeration listed there is also the corresponding DrawingML code that would be used to construct this shape were it a custom geometry. Within the construction code for each of these preset shapes there are predefined guides that the generating application shall maintain for calculation purposes at all times. The necessary guides should have the following values. Formula syntax components are defined in the fmla attribute of the gd element (§20.1.9.11).

    **3/4 of a Circle ('3cd4') - Constant value of "16200000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 270 degrees.
    
    **3/8 of a Circle ('3cd8') - Constant value of "8100000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 135 degrees.
    
    **5/8 of a Circle ('5cd8') - Constant value of "13500000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 225 degrees.
    
    **7/8 of a Circle ('7cd8') - Constant value of "18900000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 315 degrees.
    
    **Shape Bottom Edge ('b') - Constant value of "h"**
    
    :   This is the bottom edge of the shape and since the top edge of the shape is considered the 0 point, the bottom edge is thus the shape height.
    
    **1/2 of a Circle ('cd2') - Constant value of "10800000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 180 degrees.
    
    **1/4 of a Circle ('cd4') - Constant value of "5400000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 90 degrees.
    
    **1/8 of a Circle ('cd8') - Constant value of "2700000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 45 degrees.
    
    **Shape Height ('h')**
    
    :   This is the variable height of the shape defined in the shape properties. This value is received from the shape transform listed within the `<spPr>` element.
    
    **Horizontal Center ('hc') - Calculated value of "*/ w 1.0 2.0"**

    :   This is the horizontal center of the shape which is just the width divided by 2.
    
    **1/2 of Shape Height ('hd2') - Calculated value of "*/ h 1.0 2.0"**
    
    :   This is 1/2 the shape height.
    
    **1/3 of Shape Height ('hd3') - Calculated value of "*/ h 1.0 3.0"**
    
    :   This is 1/3 the shape height.
    
    **1/4 of Shape Height ('hd4') - Calculated value of "*/ h 1.0 4.0"**
    
    :   This is 1/4 the shape height.
    
    **1/5 of Shape Height ('hd5') - Calculated value of "*/ h 1.0 5.0"**

    :   This is 1/5 the shape height.
    
    **1/6 of Shape Height ('hd6') - Calculated value of "*/ h 1.0 6.0"**
    
    :   This is 1/6 the shape height.
    
    **1/8 of Shape Height ('hd8') - Calculated value of "*/ h 1.0 8.0"**
    
    :   This is 1/8 the shape height.
    
    **Shape Left Edge ('l') - Constant value of "0"**
    
    :   This is the left edge of the shape and the left edge of the shape is considered the horizontal 0 point.
    
    **Longest Side of Shape ('ls') - Calculated value of "max w h"**
    
    :   This is the longest side of the shape. This value is either the width or the height depending on which is greater.
    
    **Shape Right Edge ('r') - Constant value of "w"**

    :   This is the right edge of the shape and since the left edge of the shape is considered the 0 point, the right edge is thus the shape width.
    
    **Shortest Side of Shape ('ss') - Calculated value of "min w h"**
    
    :   This is the shortest side of the shape. This value is either the width or the height depending on which is smaller.

    **1/2 Shortest Side of Shape ('ssd2') - Calculated value of "*/ ss 1.0 2.0"**
    
    :   This is 1/2 the shortest side of the shape.
    
    **1/4 Shortest Side of Shape ('ssd4') - Calculated value of "*/ ss 1.0 4.0"**
    
    :   This is 1/4 the shortest side of the shape.
    
    **1/6 Shortest Side of Shape ('ssd6') - Calculated value of "*/ ss 1.0 6.0"**
    
    :   This is 1/6 the shortest side of the shape.
    
    **1/8 Shortest Side of Shape ('ssd8') - Calculated value of "*/ ss 1.0 8.0"**
    
    :   This is 1/8 the shortest side of the shape.
    
    **1/16 Shortest Side of Shape ('ssd16') - Calculated value of "*/ ss 1.0 16.0"**
    
    :   This is 1/16 the shortest side of the shape.
    
    **1/32 Shortest Side of Shape ('ssd32') - Calculated value of "*/ ss 1.0 32.0"**
    
    :   This is 1/32 the shortest side of the shape.
    
    **Shape Top Edge ('t') - Constant value of "0"**
    
    :   This is the top edge of the shape and the top edge of the shape is considered the vertical 0 point.
    
    **Vertical Center of Shape ('vc') - Calculated value of "*/ h 1.0 2.0"**
    
    :   This is the vertical center of the shape which is just the height divided by 2. 
    
    **Shape Width ('w')**

    :   This is the variable width of the shape defined in the shape properties. This value is received from the shape transform listed within the `<spPr>` element.

    **1/2 of Shape Width ('wd2') - Calculated value of "*/ w 1.0 2.0"**

    :   This is 1/2 the shape width.

    **1/3 of Shape Width ('wd3') - Calculated value of "*/ w 1.0 3.0"**
    
    :   This is 1/3 the shape width.
    
    **1/4 of Shape Width ('wd4') - Calculated value of "*/ w 1.0 4.0"**
    
    :   This is 1/4 the shape width.
    
    **1/5 of Shape Width ('wd5') - Calculated value of "*/ w 1.0 5.0"**
    
    :   This is 1/5 the shape width.
    
    **1/6 of Shape Width ('wd6') - Calculated value of "*/ w 1.0 6.0"**
    
    :   This is 1/6 the shape width.
    
    **1/8 of Shape Width ('wd8') - Calculated value of "*/ w 1.0 8.0"**
    
    :   This is 1/8 the shape width.
    
    **1/10 of Shape Width ('wd10') - Calculated value of "*/ w 1.0 10.0"**
    
    :   This is 1/10 the shape width.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        **accentBorderCallout1 (Callout 1 with Border and Accent Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below. 
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentBorderCallout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentBorderCallout2 (Callout 2 with Border and Accent Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentBorderCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentBorderCallout3 (Callout 3 with Border and Accent Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentBorderCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout1 (Callout 1 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout2 (Callout 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **accentCallout3 (Callout 3 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the accentCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBackPrevious (Back or Previous Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBackPrevious element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBeginning (Beginning Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBeginning element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonBlank (Blank Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonBlank element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonDocument (Document Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonDocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonEnd (End Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonEnd element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonForwardNext (Forward or Next Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonForwardNext element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonHelp (Help Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonHelp element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonHome (Home Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonHome element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonInformation (Information Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonInformation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonMovie (Movie Button Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonMovie element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonReturn (Return Button Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonReturn element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **actionButtonSound (Sound Button Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the actionButtonSound element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **arc (Curved Arc Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the arc element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentArrow (Bent Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector2 (Bent Connector 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector3 (Bent Connector 3 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector4 (Bent Connector 4 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentConnector5 (Bent Connector 5 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentConnector5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bentUpArrow (Bent Up Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bentUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bevel (Bevel Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bevel element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **blockArc (Block Arc Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the blockArc element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout1 (Callout 1 with Border Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout2 (Callout 2 with Border Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **borderCallout3 (Callout 3 with Border Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the borderCallout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bracePair (Brace Pair Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bracePair element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **bracketPair (Bracket Pair Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the bracketPair element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout1 (Callout 1 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout2 (Callout 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **callout3 (Callout 3 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the callout3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **can (Can Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the can element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartPlus (Chart Plus Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartPlus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartStar (Chart Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartStar element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chartX (Chart X Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chartX element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chevron (Chevron Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chevron element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **chord (Chord Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the chord element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **circularArrow (Circular Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the circularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cloud (Cloud Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cloud element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cloudCallout (Callout Cloud Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cloudCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **corner (Corner Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the corner element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cornerTabs (Corner Tabs Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cornerTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **cube (Cube Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the cube element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector2 (Curved Connector 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector3 (Curved Connector 3 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector3 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector4 (Curved Connector 4 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedConnector5 (Curved Connector 5 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedConnector5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedDownArrow (Curved Down Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedDownArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedLeftArrow (Curved Left Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedLeftArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedRightArrow (Curved Right Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **curvedUpArrow (Curved Up Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the curvedUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **decagon (Decagon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the decagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **diagStripe (Diagonal Stripe Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the diagStripe element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **diamond (Diamond Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the diamond element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **dodecagon (Dodecagon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the dodecagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **donut (Donut Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the donut element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **doubleWave (Double Wave Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the doubleWave element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **downArrow (Down Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the downArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **downArrowCallout (Callout Down Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the downArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipse (Ellipse Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipse element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipseRibbon (Ellipse Ribbon Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipseRibbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ellipseRibbon2 (Ellipse Ribbon 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ellipseRibbon2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartAlternateProcess (Alternate Process Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartAlternateProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartCollate (Collate Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartCollate element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartConnector (Connector Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartConnector element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDecision (Decision Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDecision element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDelay (Delay Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDelay element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDisplay (Display Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDisplay (Display Flow Shape) element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartDocument (Document Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartDocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartExtract (Extract Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartExtract element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartInputOutput (Input Output Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartInputOutput element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartInternalStorage (Internal Storage Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartInternalStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticDisk (Magnetic Disk Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticDisk element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticDrum (Magnetic Drum Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticDrum element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMagneticTape (Magnetic Tape Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMagneticTape element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartManualInput (Manual Input Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartManualInput element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartManualOperation (Manual Operation Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartManualOperation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMerge (Merge Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMerge element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartMultidocument (Multi-Document Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartMultidocument element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOfflineStorage (Offline Storage Flow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOfflineStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOffpageConnector (Off-Page Connector Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOffpageConnector element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOnlineStorage (Online Storage Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOnlineStorage element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartOr (Or Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartOr element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPredefinedProcess (Predefined Process Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPredefinedProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPreparation (Preparation Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPreparation element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartProcess (Process Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartProcess element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPunchedCard (Punched Card Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPunchedCard element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartPunchedTape (Punched Tape Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartPunchedTape element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartSort (Sort Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartSort element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartSummingJunction (Summing Junction Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartSummingJunction element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **flowChartTerminator (Terminator Flow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the flowChartTerminator element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **foldedCorner (Folded Corner Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the foldedCorner element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **frame (Frame Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the frame element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **funnel (Funnel Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the funnel element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **gear6 (Gear 6 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the gear6 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **gear9 (Gear 9 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the gear9 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **halfFrame (Half Frame Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the halfFrame element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **heart (Heart Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the heart element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **heptagon (Heptagon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the heptagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **hexagon (Hexagon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the hexagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **homePlate (Home Plate Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the homePlate element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **horizontalScroll (Horizontal Scroll Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the horizontalScroll element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **irregularSeal1 (Irregular Seal 1 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the irregularSeal1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **irregularSeal2 (Irregular Seal 2 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the irregularSeal2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftArrow (Left Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftArrowCallout (Callout Left Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftBrace (Left Brace Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftBrace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftBracket (Left Bracket Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftBracket element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftCircularArrow (Left Circular Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftCircularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightArrow (Left Right Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightArrowCallout (Callout Left Right Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightCircularArrow (Left Right Circular Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightCircularArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightRibbon (Left Right Ribbon Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightRibbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftRightUpArrow (Left Right Up Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftRightUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **leftUpArrow (Left Up Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the leftUpArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **lightningBolt (Lightning Bolt Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the lightningBolt element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **line (Line Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the line element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **lineInv (Line Inverse Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the lineInv element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathDivide (Divide Math Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathDivide element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathEqual (Equal Math Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathEqual element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathMinus (Minus Math Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathMinus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathMultiply (Multiply Math Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathMultiply element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathNotEqual (Not Equal Math Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathNotEqual element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **mathPlus (Plus Math Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the mathPlus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **moon (Moon Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the moon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **nonIsoscelesTrapezoid (Non-Isosceles Trapezoid Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the nonIsoscelesTrapezoid element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **notchedRightArrow (Notched Right Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the notchedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **octagon (Octagon Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the octagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **parallelogram (Parallelogram Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the parallelogram element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pentagon (Pentagon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pentagon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pie (Pie Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pie element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **pieWedge (Pie Wedge Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the pieWedge element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plaque (Plaque Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plaque element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plaqueTabs (Plaque Tabs Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plaqueTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **plus (Plus Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the plus element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **quadArrow (Quad-Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the quadArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **quadArrowCallout (Callout Quad-Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the quadArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rect (Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ribbon (Ribbon Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ribbon element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **ribbon2 (Ribbon 2 Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the ribbon2 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightArrow (Right Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightArrowCallout (Callout Right Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightBrace (Right Brace Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightBrace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rightBracket (Right Bracket Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rightBracket element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round1Rect (One Round Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round1Rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round2DiagRect (Two Diagonal Round Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round2DiagRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **round2SameRect (Two Same-side Round Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the round2SameRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **roundRect (Round Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the roundRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **rtTriangle (Right Triangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the rtTriangle element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **smileyFace (Smiley Face Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the smileyFace element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip1Rect (One Snip Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip1Rect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip2DiagRect (Two Diagonal Snip Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip2DiagRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snip2SameRect (Two Same-side Snip Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snip2SameRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **snipRoundRect (One Snip One Round Corner Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the snipRoundRect element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **squareTabs (Square Tabs Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the squareTabs element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star10 (Ten Pointed Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star10 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star12 (Twelve Pointed Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star12 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star16 (Sixteen Pointed Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star16 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star24 (Twenty Four Pointed Star Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star24 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star32 (Thirty Two Pointed Star Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star32 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star4 (Four Pointed Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star4 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star5 (Five Pointed Star Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star5 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star6 (Six Pointed Star Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star6 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star7 (Seven Pointed Star Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star7 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **star8 (Eight Pointed Star Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the star8 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **straightConnector1 (Straight Connector 1 Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the straightConnector1 element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **stripedRightArrow (Striped Right Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the stripedRightArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **sun (Sun Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the sun element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **swooshArrow (Swoosh Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the swooshArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **teardrop (Teardrop Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the teardrop element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **trapezoid (Trapezoid Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the trapezoid element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **triangle (Triangle Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the triangle element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upArrow (Up Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upArrowCallout (Callout Up Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upDownArrow (Up Down Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upDownArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **upDownArrowCallout (Callout Up Down Arrow Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the upDownArrowCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **uturnArrow (U-Turn Arrow Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the uturnArrow element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **verticalScroll (Vertical Scroll Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the verticalScroll element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wave (Wave Shape) **

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wave element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeEllipseCallout (Callout Wedge Ellipse Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeEllipseCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeRectCallout (Callout Wedge Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeRectCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        **wedgeRoundRectCallout (Callout Wedge Round Rectangle Shape)**

        :   Specifies a preset shape geometry. This geometry shall be designed to match the normative image below.
        
            [Note: An example of DrawingML which can be used to generate this preset shape definition is contained in the wedgeRoundRectCallout element in the preset shape geometries electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

            ![123](./imgs/aaa.png)

        [Note: The W3C XML Schema definition of this simple type’s content model (ST_ShapeType) is located in §A.4.1. end note]

## 20.1.10.57 ST_StyleMatrixColumnIndex (样式矩阵列索引)

=== "中文"

    这个简单类型指定了一个索引，该索引指向由`fmtScheme`元素（`bgFillStyleLst`、`effectStyleLst`、`fillStyleLst`或`lnStyleLst`）指定的样式矩阵中的一个列表。
    
    这个简单类型的内容是对W3C XML Schema中`unsignedInt`数据类型的限制。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_StyleMatrixColumnIndex) is located in §A.4.1. end note]

=== "英文"

    **ST_StyleMatrixColumnIndex (Style Matrix Column Index)**

    This simple type specifies an index into one of the lists in the style matrix specified by the fmtScheme element (bgFillStyleLst, effectStyleLst, fillStyleLst, or lnStyleLst).

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_StyleMatrixColumnIndex) is located in §A.4.1. end note]

## 20.1.10.58 ST_SystemColorVal (系统颜色值)

=== "中文"

    这个简单类型指定了系统颜色值。该颜色基于文档所在系统中该颜色当前的值。

    应用程序应使用`lastClr`属性来确定最后使用的颜色的绝对值，如果不支持系统颜色。
    
    这个简单类型的内容是对W3C XML Schema中`token`数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **3dDkShadow**（3D深色系统颜色）：指定三维显示元素的深色阴影颜色。
    - **3dLight**（3D亮色系统颜色）：指定三维显示元素的亮色（面向光源的边缘）。
    - **activeBorder**（活动边框系统颜色）：指定活动窗口边框颜色。
    - **activeCaption**（活动标题系统颜色）：指定活动窗口标题栏颜色，特别是如果启用了渐变效果，则为渐变的标题栏的左侧颜色。
    - **appWorkspace**（应用程序工作区系统颜色）：指定多文档界面（MDI）应用程序的背景颜色。
    - **background**（背景系统颜色）：指定桌面背景颜色。
    - **btnFace**（按钮表面系统颜色）：指定三维显示元素和对话框框背景的表面颜色。
    - **btnHighlight**（按钮高亮系统颜色）：指定三维显示元素的高亮颜色（面向光源的边缘）。
    - **btnShadow**（按钮阴影系统颜色）：指定三维显示元素的阴影颜色（背离光源的边缘）。
    - **btnText**（按钮文本系统颜色）：指定按下按钮上的文本颜色。
    - **captionText**（标题文本系统颜色）：指定标题、大小框和滚动条箭头框的文本颜色。
    - **gradientActiveCaption**（渐变活动标题系统颜色）：指定活动窗口标题栏渐变的右侧颜色。
    - **gradientInactiveCaption**（渐变非活动标题系统颜色）：指定非活动窗口标题栏渐变的右侧颜色。
    - **grayText**（灰色文本系统颜色）：指定灰色（禁用）文本。如果当前显示驱动程序不支持纯灰色，则此颜色设置为0。
    - **highlight**（高亮系统颜色）：指定在控件中选择的项目的颜色。
    - **highlightText**（高亮文本系统颜色）：指定在控件中选择的项目的文本颜色。
    - **hotLight**（热点亮系统颜色）：指定超链接或热跟踪项的颜色。
    - **inactiveBorder**（非活动边框系统颜色）：指定非活动窗口边框的颜色。
    - **inactiveCaption**（非活动标题系统颜色）：指定非活动窗口标题栏的颜色，特别是如果启用了渐变效果，则为渐变的标题栏的左侧颜色。
    - **inactiveCaptionText**（非活动标题文本系统颜色）：指定非活动标题中的文本颜色。
    - **infoBk**（信息背景系统颜色）：指定工具提示控件的背景颜色。
    - **infoText**（信息文本系统颜色）：指定工具提示控件的文本颜色。
    - **menu**（菜单系统颜色）：指定菜单的背景颜色。
    - **menuBar**（菜单栏系统颜色）：指定菜单以平面样式显示时菜单栏的背景颜色。
    - **menuHighlight**（菜单高亮系统颜色）：指定在菜单以平面样式显示时用于突出显示菜单项的颜色。
    - **menuText**（菜单文本系统颜色）：指定菜单中文本的颜色。
    - **scrollBar**（滚动条系统颜色）：指定滚动条灰色区域的颜色。
    - **window**（窗口系统颜色）：指定窗口背景颜色。
    - **windowFrame**（窗口框架系统颜色）：指定窗口框架的颜色。
    - **windowText**（窗口文本系统颜色）：指定窗口中文本的颜色。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SystemColorVal) is located in §A.4.1. end note]

=== "英文"

    **ST_SystemColorVal (System Color Value)**

    This simple type specifies a system color value. This color is based upon the value that this color currently has within the system on which the document is being viewed.

    Applications shall use the lastClr attribute to determine the absolute value of the last color used if system colors are not supported.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        - **3dDkShadow** (3D Dark System Color) Specifies a Dark shadow color for three-dimensional display elements.
        - **3dLight** (3D Light System Color) Specifies a Light color for three-dimensional display elements (for edges facing the light source).
        - **activeBorder** (Active Border System Color) Specifies an Active Window Border Color.
        - **activeCaption** (Active Caption System Color) Specifies the active window title bar color. In particular the left side color in the color gradient of an active window's title bar if the gradient effect is enabled.
        - **appWorkspace** (Application Workspace System Color) Specifies the Background color of multiple document interface (MDI) applications.
        - **background** (Background System Color) Specifies the desktop background color.
        - **btnFace** (Button Face System Color) Specifies the face color for three-dimensional display elements and for dialog box backgrounds.
        - **btnHighlight** (Button Highlight System Color) Specifies the highlight color for three-dimensional
        - **display** elements (for edges facing the light source).
        - **btnShadow** (Button Shadow System Color) Specifies the shadow color for three-dimensional display elements (for edges facing away from the light source).
        - **btnText** (Button Text System Color) Specifies the color of text on push buttons.
        - **captionText** (Caption Text System Color) Specifies the color of text in the caption, size box, and scroll bar arrow box.
        - **gradientActiveCaption** (Gradient Active Caption System Color) Specifies the right side color in the color gradient of an active window's title bar.
        - **gradientInactiveCaption** (Gradient Inactive Caption System Color) Specifies the right side color in the color gradient of an inactive window's title bar.
        - **grayText** (Gray Text System Color) Specifies a grayed (disabled) text. This color is set to 0 if the current display driver does not support a solid gray color.
        - **highlight** (Highlight System Color) Specifies the color of Item(s) selected in a control.
        - **highlightText** (Highlight Text System Color) Specifies the text color of item(s) selected in a control.
        - **hotLight** (Hot Light System Color) Specifies the color for a hyperlink or hot-tracked item.
        - **inactiveBorder** (Inactive Border System Color) Specifies the color of the Inactive window border.
        - **inactiveCaption** (Inactive Caption System Color) Specifies the color of the Inactive window caption. Specifies the left side color in the color gradient of an inactive window's title bar if the gradient effect is enabled.
        - **inactiveCaptionText** (Inactive Caption Text System Color) Specifies the color of text in an inactive caption.
        - **infoBk** (Info Back System Color) Specifies the background color for tooltip controls.
        - **infoText** (Info Text System Color) Specifies the text color for tooltip controls.
        - **menu** (Menu System Color) Specifies the menu background color.
        - **menuBar** (Menu Bar System Color) Specifies the background color for the menu bar when menus appear as flat menus.
        - **menuHighlight** (Menu Highlight System Color) Specifies the color used to highlight menu items when the menu appears as a flat menu.
        - **menuText** (Menu Text System Color) Specifies the color of Text in menus.
        - **scrollBar** (Scroll Bar System Color) Specifies the scroll bar gray area color.
        - **window** (Window System Color) Specifies window background color.
        - **windowFrame** (Window Frame System Color) Specifies the window frame color.
        - **windowText** (Window Text System Color) Specifies the color of text in windows.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SystemColorVal) is located in §A.4.1. end note]

## 20.1.10.59 ST_TextAlignType (文本对齐类型)

=== "中文"

    这个简单类型指定了文本对齐类型。

    这个简单类型的内容是对W3C XML Schema中`token`数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    **枚举**
    
    - **ctr**（文本对齐枚举（居中））：将文本居中对齐。
    - **dist**（文本对齐枚举（分布式））：将文本单词分布在整个文本行上。
    - **just**（文本对齐枚举（两端对齐））：使文本在整行上两端对齐。它是智能的，不会对短句进行两端对齐。
    - **justLow**（文本对齐枚举（调整低））：使用调整后的Kashida长度对阿拉伯文本进行对齐。
    - **l**（文本对齐枚举（左对齐））：将文本与左边距对齐。
    - **r**（文本对齐枚举（右对齐））：将文本与右边距对齐。
    - **thaiDist**（文本对齐枚举（泰语分布式））：特别分布泰文文本，因为每个字符都被视为一个单词。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAlignType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextAlignType (Text Alignment Types)**

    This simple type specifies the text alignment types

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    - **ctr** (Text Alignment Enum ( Center )) Align text in the center.
    - **dist** (Text Alignment Enum ( Distributed )) Distributes the text words across an entire text line.
    - **just** (Text Alignment Enum ( Justified )) Align text so that it is justified across the whole line. It is smart in the sense that it does not justify sentences which are short.
    - **justLow** (Text Alignment Enum ( Justified Low )) Aligns the text with an adjusted kashida length for Arabic text.
    - **l** (Text Alignment Enum ( Left )) Align text to the left margin.
    - **r** (Text Alignment Enum ( Right )) Align text to the right margin.
    - **thaiDist** (Text Alignment Enum ( Thai Distributed )) Distributes Thai text specially, because each character is treated as a word.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAlignType) is located in §A.4.1. end note]

## 20.1.10.60 ST_TextAnchoringType (文本锚定类型)

=== "中文"

    这个简单类型指定了文本可用的锚定类型列表。

    这个简单类型的内容是对W3C XML Schema中`token`数据类型的限制。

    这个简单类型被限制为以下表格中列出的值：

    **枚举**

    - **b**（文本锚定枚举（底部））：将文本锚定在边界矩形的底部。
    
    - **ctr**（文本锚定枚举（居中））：将文本锚定在边界矩形的中间。
    
    - **dist**（文本锚定枚举（分布式））：以垂直方向分布文本。当文本是水平的时候，这会拉开实际的文本行，几乎总是与anchorJustified相同（特殊情况：如果只有1行，那么锚定在中间）。当文本是垂直的时候，它会在垂直方向分布字母。这与anchorJustified不同，因为它总是强制分布单词，即使一行只有一个或两个单词。

    - **just**（文本锚定枚举（两端对齐））：将文本锚定，使其在垂直方向上两端对齐。当文本是水平的时候，这会拉开实际的文本行，几乎总是与'distrib'相同（特殊情况：如果只有1行，那么锚定在顶部）。当文本是垂直的时候，它会在垂直方向上两端对齐字母。这与anchorDistributed不同，因为在某些情况下，比如一行很少文本的情况下，它不会对齐。

    - **t**（文本锚定类型枚举（顶部））：将文本锚定在边界矩形的顶部。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAnchoringType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextAnchoringType (Text Anchoring Types)**

    This simple type specifies a list of available anchoring types for text.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **b** (Text Anchor Enum ( Bottom )) 
    
    :   Anchor the text at the bottom of the bounding rectangle.

    **ctr** (Text Anchor Enum ( Center )) 
    
    :   Anchor the text at the middle of the bounding rectangle.

    **dist** (Text Anchor Enum ( Distributed )) 
    
    :   Anchor the text so that it is distributed vertically. When text is horizontal, this spaces out the actual lines of text and is almost always identical in behavior to anchorJustified (special case: if only 1 line, then anchored in middle). When text is vertical, then it distributes the letters vertically. This is different than anchorJustified, because it always forces distribution of the words, even if there are only one or two words in a line.

    **just** (Text Anchor Enum ( Justified )) 
    
    :   Anchor the text so that it is justified vertically. When text is horizontal, this spaces out the actual lines of text and is almost always identical in behavior to 'distrib' (special case: if only 1 line, then anchored at top). When text is vertical, then it justifies the letters vertically. This is different than anchorDistributed, because in some cases such as very little text in a line, it does not justify.

    **t** (Text Anchoring Type Enum ( Top )) 
    
    :   Anchor the text at the top of the bounding rectangle.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAnchoringType) is located in §A.4.1. end note]

## 20.1.10.61 ST_TextAutonumberScheme (文本自动编号方案)

=== "中文"

    这个简单类型指定了自动编号方案的列表。

    这个简单类型的内容是对W3C XML Schema中`token`数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    **枚举**
    
    - **alphaLcParenBoth**（自动编号枚举（小写字母括号两边））
 
    :   (a), (b), (c), …
    
    - **alphaLcParenR**（自动编号枚举（小写字母右括号））
 
    :   a), b), c), …
    
    - **alphaLcPeriod**（自动编号枚举（小写字母句点））
 
    :   a., b., c., …
    
    - **alphaUcParenBoth**（自动编号枚举（大写字母括号两边））
 
    :   (A), (B), (C), …
    
    - **alphaUcParenR**（自动编号枚举（大写字母右括号））
 
    :   A), B), C), …
    
    - **alphaUcPeriod**（自动编号枚举（大写字母句点））
 
    :   A., B., C., …
    
    - **arabic1Minus**（自动编号枚举（阿拉伯数字1带负号））
 
    :   双向阿拉伯数字1（AraAlpha），带有ANSI减号符号
    
    - **arabic2Minus**（自动编号枚举（阿拉伯数字2带负号））
 
    :   双向阿拉伯数字2（AraAbjad），带有ANSI减号符号
    
    - **arabicDbPeriod**（自动编号枚举（双字节阿拉伯数字带双字节句点））
 
    :   双字节阿拉伯数字带有双字节句点
    
    - **arabicDbPlain**（自动编号枚举（双字节阿拉伯数字））
 
    :   双字节阿拉伯数字
    
    - **arabicParenBoth**（自动编号枚举（阿拉伯数字括号两边））
 
    :   (1), (2), (3), …
    
    - **arabicParenR**（自动编号枚举（阿拉伯数字右括号））
 
    :   1), 2), 3), …
    
    - **arabicPeriod**（自动编号枚举（阿拉伯数字句点））
 
    :   1., 2., 3., …
    
    - **arabicPlain**（自动编号枚举（阿拉伯数字））
 
    :   1, 2, 3, …
    
    - **circleNumDbPlain**（自动编号枚举（双字节圆圈数字））
 
    :   双字节圆圈数字（1-10 圆圈[0x2460-]，11-阿拉伯数字）
    
    - **circleNumWdBlackPlain**（自动编号枚举（Wingdings黑色圆圈数字））
 
    :   Wingdings黑色圆圈数字
    
    - **circleNumWdWhitePlain**（自动编号枚举（Wingdings白色圆圈数字））
 
    :   Wingdings白色圆圈数字（0-10 圆圈[0x0080-]，11-阿拉伯数字）
    
    - **ea1ChsPeriod**（自动编号枚举（EA：简体中文带单字节句点））
 
    :   EA：简体中文带单字节句点
    
    - **ea1ChsPlain**（自动编号枚举（EA：简体中文））
 
    :   EA：简体中文（TypeA 1-99，TypeC 100-）
    
    - **ea1ChtPeriod**（自动编号枚举（EA：繁体中文带单字节句点））
 
    :   EA：繁体中文带单字节句点
    
    - **ea1ChtPlain**（自动编号枚举（EA：繁体中文））
 
    :   EA：繁体中文（TypeA 1-19，TypeC 20-）
    
    - **ea1JpnChsDbPeriod**（自动编号枚举（EA：日语/简体中文带双字节句点））
 
    :   EA：日语带双字节句点
    
    - **ea1JpnKorPeriod**（自动编号枚举（EA：日语/韩语带单字节句点））
 
    :   EA：日语/韩语带单字节句点
    
    - **ea1JpnKorPlain**（自动编号枚举（EA：日语/韩语））
 
    :   EA：日语/韩语（TypeC 1-）
    
    - **hebrew2Minus**（自动编号枚举（希伯来语2带负号））
 
    :   双向希伯来语2带ANSI减号
    
    - **hindiAlpha1Period**（自动编号枚举（印地语字母1带句点））
 
    :   印地语字母句点 - 辅音
    
    - **hindiAlphaPeriod**（自动编号枚举（印地语字母带句点））
 
    :   印地语字母句点 - 元音
    
    - **hindiNumParenR**（自动编号枚举（印地数字右括号））
 
    :   印地数字右括号
    
    - **hindiNumPeriod**（自动编号枚举（印地数字句点））
 
    :   印地数字句点
    
    - **romanLcParenBoth**（自动编号枚举（罗马字母小写括号两边））
 
    :   (i), (ii), (iii), …
    
    - **romanLcParenR**（自动编号枚举（罗马字母小写右括号））
 
    :   i), ii), iii), …
    
    - **romanLcPeriod**（自动编号枚举（罗马字母小写句点））
 
    :   i., ii., iii., …
    
    - **romanUcParenBoth**（自动编号枚举（罗马字母大写括号两边））
 
    :   (I), (II), (III), …
    
    - **romanUcParenR**（自动编号枚举（罗马字母大写右括号））
 
    :   I), II), III), …
    
    - **romanUcPeriod**（自动编号枚举（罗马字母大写句点））
 
    :   I., II., III., …
    
    - **thaiAlphaParenBoth**（自动编号枚举（泰文字母括号两边））
 
    :   泰文字母括号 - 两边
    
    - **thaiAlphaParenR**（自动编号枚举（泰文字母右括号））
 
    :   泰文字母括号 - 右边
    
    - **thaiAlphaPeriod**（自动编号枚举（泰文字母句点））
 
    :   泰文字母句点
    
    - **thaiNumParenBoth**（自动编号枚举（泰文数字括号两边））
 
    :   泰文数字括号 - 两边
    
    - **thaiNumParenR**（自动编号枚举（泰文数字右括号））
 
    :   泰文数字括号 - 右边
    
    - **thaiNumPeriod**（自动编号枚举（泰文数字句点））
 
    :   泰文数字句点

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAutonumberScheme) is located in §A.4.1. end note]

=== "英文"

    **ST_TextAutonumberScheme (Text Auto-number Schemes)**

    This simple type specifies a list of automatic numbering schemes.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    alphaLcParenBoth (Autonumber Enum (alphaLcParenBoth ))
    
    :   (a), (b), (c), …

    alphaLcParenR (Autonumbering Enum (alphaLcParenR ))

    :   a), b), c), …
    
    alphaLcPeriod (Autonumbering Enum ( alphaLcPeriod))
    
    :   a., b., c., …
    
    alphaUcParenBoth (Autonumbering Enum (alphaUcParenBoth ))
    
    :   (A), (B), (C), …
    
    alphaUcParenR (Autonumbering Enum (alphaUcParenR ))
    
    :   A), B), C), …
    
    alphaUcPeriod (Autonumbering Enum (alphaUcPeriod ))
    
    :   A., B., C., …
    
    arabic1Minus (Autonumbering Enum ( arabic1Minus))
    
    :   Bidi Arabic 1 (AraAlpha) with ANSI minus symbol
    
    arabic2Minus (Autonumbering Enum ( arabic2Minus))
    
    :   Bidi Arabic 2 (AraAbjad) with ANSI minus symbol
    
    arabicDbPeriod (Autonumbering Enum (arabicDbPeriod ))
    
    :   Dbl-byte Arabic numbers w/ double-byte period
    
    arabicDbPlain (Autonumbering Enum ( arabicDbPlain))
    
    :   Dbl-byte Arabic numbers
    
    arabicParenBoth (Autonumbering Enum (arabicParenBoth ))
    
    :   (1), (2), (3), …
    
    arabicParenR (Autonumbering Enum ( arabicParenR )) 
    
    :   1), 2), 3), …
    
    arabicPeriod (Autonumbering Enum ( arabicPeriod )) 
    
    :   1., 2., 3., …
    
    arabicPlain (Autonumbering Enum ( arabicPlain )) 
    
    :   1, 2, 3, …
    
    circleNumDbPlain (Autonumbering Enum ( circleNumDbPlain ))
    
    :   Dbl-byte circle numbers (1-10 circle[0x2460-], 11-arabic numbers)

    circleNumWdBlackPlain (Autonumbering Enum (circleNumWdBlackPlain ))

    :   Wingdings black circle numbers

    circleNumWdWhitePlain (Autonumbering Enum (circleNumWdWhitePlain ))

    :   Wingdings white circle numbers (0-10 circle[0x0080-],11- arabic numbers)

    ea1ChsPeriod (Autonumbering Enum ( ea1ChsPeriod))

    :   EA: Simplified Chinese w/ single-byte period

    ea1ChsPlain (Autonumbering Enum ( ea1ChsPlain )) 
    
    :   EA: Simplified Chinese (TypeA 1-99, TypeC 100-)

    ea1ChtPeriod (Autonumbering Enum ( ea1ChtPeriod))

    :   EA: Traditional Chinese w/ single-byte period

    ea1ChtPlain (Autonumbering Enum ( ea1ChtPlain )) 
    
    :   EA: Traditional Chinese (TypeA 1-19, TypeC 20-)

    ea1JpnChsDbPeriod (Autonumbering Enum (ea1JpnChsDbPeriod ))

    :   EA: Japanese w/ double-byte period

    ea1JpnKorPeriod (Autonumbering Enum (ea1JpnKorPeriod ))

    :   EA: Japanese/Korean w/ single-byte period

    ea1JpnKorPlain (Autonumbering Enum (ea1JpnKorPlain ))

    :   EA: Japanese/Korean (TypeC 1-)

    hebrew2Minus (Autonumbering Enum (hebrew2Minus ))

    :   Bidi Hebrew 2 with ANSI minus symbol

    hindiAlpha1Period (Autonumbering Enum (hindiAlpha1Period ))

    :   Hindi alphabet period - consonants

    hindiAlphaPeriod (Autonumbering Enum (hindiAlphaPeriod ))

    :   Hindi alphabet period - vowels

    hindiNumParenR (Autonumbering Enum (hindiNumParenR ))

    :   Hindi numerical parentheses - right

    hindiNumPeriod (Autonumbering Enum (hindiNumPeriod ))

    :   Hindi numerical period

    romanLcParenBoth (Autonumbering Enum (romanLcParenBoth ))

    :   (i), (ii), (iii), …

    romanLcParenR (Autonumbering Enum (romanLcParenR ))

    :   i), ii), iii), …

    romanLcPeriod (Autonumbering Enum (romanLcPeriod ))

    :   i., ii., iii., …

    romanUcParenBoth (Autonumbering Enum (romanUcParenBoth ))

    :   (I), (II), (III), …

    romanUcParenR (Autonumbering Enum (romanUcParenR ))

    :   I), II), III), …

    romanUcPeriod (Autonumbering Enum (romanUcPeriod ))

    :   I., II., III., …

    thaiAlphaParenBoth (Autonumbering Enum ( thaiAlphaParenBoth ))

    :   Thai alphabet parentheses - both

    thaiAlphaParenR (Autonumbering Enum (thaiAlphaParenR ))

    :   Thai alphabet parentheses - right

    thaiAlphaPeriod (Autonumbering Enum (thaiAlphaPeriod ))

    :   Thai alphabet period

    thaiNumParenBoth (Autonumbering Enum (thaiNumParenBoth ))

    :   Thai numerical parentheses - both

    thaiNumParenR (Autonumbering Enum (thaiNumParenR ))

    :   Thai numerical parentheses - right

    thaiNumPeriod (Autonumbering Enum (thaiNumPeriod ))

    :   Thai numerical period

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextAutonumberScheme) is located in §A.4.1. end note]

## 20.1.10.62 ST_TextBulletSizePercent (项目符号百分比)

=== "中文"

    这个简单类型指定了项目符号百分比的范围。项目符号百分比是指项目符号相对于应该跟随它的文本的大小。

    这个简单类型还指定了以下限制：
    
    - 这个简单类型的内容应该匹配以下正则表达式模式：`0*((2[5-9])|([3-9][0-9])|([1-3][0-9][0-9])|400)%`。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletSizePercent) is located in §A.4.1. end note]

=== "英文"

    **ST_TextBulletSizePercent (Bullet Size Percentage)**

    This simple type specifies the range that the bullet percent can be. A bullet percent is the size of the bullet with respect to the text that should follow it.

    This simple type also specifies the following restrictions:

    - This simple type’s contents shall match the following regular expression pattern: 0*((2[5-9])|([3-9][0-9])|([1-3][0-9][0-9])|400)%.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletSizePercent) is located in §A.4.1. end note]

## 20.1.10.63 ST_TextBulletStartAtNum (项目符号起始编号范围)

=== "中文"

    这个简单类型指定了项目符号的自动编号序列的起始编号范围。当编号是按字母顺序时，数字映射到相应的字母。1->a，2->b等。如果数字超过26，那么数字开始重复。例如，27->aa，53->aaa。

    这个简单类型的内容是对W3C XML Schema int 数据类型的限制。
    
    这个简单类型还指定了以下限制：
    
    - 这个简单类型的最小值大于或等于1。
    - 这个简单类型的最大值小于或等于32767。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletStartAtNum) is located in §A.4.1. end note]

=== "英文"

    **ST_TextBulletStartAtNum (Start Bullet At Number)**

    This simple type specifies the range that the start at number for a bullet's auto-numbering sequence can begin at. When the numbering is alphabetical, then the numbers map to the appropriate letter. 1->a, 2->b, etc. If the numbers go above 26, then the numbers begin to double up. For example, 27->aa and 53->aaa.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 1.
    - This simple type has a maximum value of less than or equal to 32767.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletStartAtNum) is located in §A.4.1. end note]

## 20.1.10.64 ST_TextCapsType (文本大写类型)

=== "中文"

    这个简单类型指定了文本的大写类型。

    这个简单类型的内容是对W3C XML Schema token 数据类型的限制。
    
    这个简单类型被限制为以下表中列出的值：
    
    - **all**（Text Caps Enum（全部））
      
        将全部文字转换为大写。即使它们在后台存储中以不同的方式存储，所有小写字母也会转换为大写。
    
    - **none**（Text Caps Enum（无））
      
        我们不能隐式地将noCaps设为未指定大写的场景，因为不指定意味着从特定样式派生，用户可能想要覆盖并使一些文本不具有大写方案，即使样式要求不同。
    
    - **small**（Text Caps Enum（小写））
      
        对文本应用小写。所有字母都转换为小写。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextCapsType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextCapsType (Text Cap Types)**

    This simple type specifies the cap types of the text.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **all** (Text Caps Enum ( All )) 
    
    :   Apply all caps on the text. All lower case letters are converted to upper case even though they are stored differently in the backing store.

    **none** (Text Caps Enum ( None )) 
    
    :   The reason we cannot implicitly have noCaps be the scenario where capitalization is not specified is because not being specified implies deriving from a particular style and the user might want to override that and make some text not have a capitalization scheme even though the style says otherwise.

    **small** (Text Caps Enum ( Small )) 
    
    :   Apply small caps to the text. All letters are converted to lower case.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextCapsType) is located in §A.4.1. end note]

## 20.1.10.65 ST_TextColumnCount (文本列数)

=== "中文"

    这个简单类型指定了列的数量。

    这个简单类型的内容是对W3C XML Schema int 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 这个简单类型的最小值大于或等于1。
    - 这个简单类型的最大值小于或等于16。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextColumnCount) is located in §A.4.1. end note]

=== "英文"

    **ST_TextColumnCount (Text Column Count)**

    This simple type specifies the number of columns.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 1.
    - This simple type has a maximum value of less than or equal to 16.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextColumnCount) is located in §A.4.1. end note]

## 20.1.10.66 ST_TextFontAlignType (文本字体对齐方式)

=== "中文"

    这个简单类型指定了不同类型的字体对齐方式。

    这个简单类型的内容是对W3C XML Schema token 数据类型的限制。
    
    这个简单类型受限于以下表格中列出的值：
    
    - **auto** (字体对齐枚举 (自动)) ：当文本流是水平或简单垂直时，与字体基线相同，但对于其他垂直模式，与字体中心相同。
    - **b** (字体对齐枚举 (底部)) ：字母锚定在单行的底部。这与底部基线不同，因为包括字母 "g," "q," "y," 等。
    - **base** (字体对齐枚举 (基线)) ：字母锚定在单行的底部基线上。
    - **ctr** (字体对齐枚举 (中心)) ：字母锚定在单行的两个基线之间。
    - **t** (字体对齐枚举 (顶部)) ：字母锚定在单行的顶部基线上。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontAlignType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextFontAlignType (Font Alignment Types)**

    This simple type specifies the different kinds of font alignment.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **auto** (Font Alignment Enum ( Automatic )) 
    
    :   When the text flow is horizontal or simple vertical same as fontBaseline but for other vertical modes same as fontCenter.

    **b** (Font Alignment Enum ( Bottom )) 
    
    :   The letters are anchored to the very bottom of a single line. This is different than the bottom baseline because of letters such as "g," "q," "y," etc.

    **base** (Font Alignment Enum ( Baseline )) 
    
    :   The letters are anchored to the bottom baseline of a single line.

    **ctr** (Font Alignment Enum ( Center )) 
    
    :   The letters are anchored between the two baselines of a single line.

    **t** (Font Alignment Enum ( Top )) 
    
    :   The letters are anchored to the top baseline of a single line.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontAlignType) is located in §A.4.1. end note]

## 20.1.10.67 ST_TextFontScalePercentOrPercentString (文本字体缩放百分比)

=== "中文"

    这个简单类型指定其内容将包含一个文本字体缩放百分比。有关详细信息，请参阅联合体的成员类型。

    这个简单类型是以下类型的联合体：
    
    - ST_Percentage 简单类型 (§22.9.2.9)。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontScalePercentOrPercentString) is located in §A.4.1. end note]

=== "英文"

    **ST_TextFontScalePercentOrPercentString (Text Font Scale Percentage)**

    This simple type specifies that its contents will contain a text font scale percent percentage. See the union's member types for details.

    This simple type is a union of the following types:

    - The ST_Percentage simple type (§22.9.2.9).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontScalePercentOrPercentString) is located in §A.4.1. end note]

## 20.1.10.68 ST_TextFontSize (文本字体尺寸)

=== "中文"

    这个简单类型指定任何文本的大小，单位为百分之一磅。必须至少为1磅。

    这个简单类型的内容是对W3C XML Schema int数据类型的限制。
    
    此简单类型还指定了以下限制：
    
    - 此简单类型的最小值大于或等于100。
    - 此简单类型的最大值小于或等于400000。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontSize) is located in §A.4.1. end note]

=== "英文"

    **ST_TextFontSize (Text Font Size)**

    This simple type specifies the size of any text in hundredths of a point. Shall be at least 1 point.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 100.
    - This simple type has a maximum value of less than or equal to 400000.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextFontSize) is located in §A.4.1. end note]

## 20.1.10.69 ST_TextHorzOverflowType (文本水平溢出类型)

=== "中文"

    这个简单类型指定文本的水平溢出类型。

    这个简单类型的内容是对W3C XML Schema token数据类型的限制。
    
    此简单类型限制为以下表中列出的值：
    
    **clip**（Text Horizontal Overflow Enum（裁剪））
    
        :   当一个大字符无法放入一行时，在适当的水平溢出处裁剪它。
    
    **overflow**（Text Horizontal Overflow Enum（溢出））
    
        :   当一个大字符无法放入一行时，允许水平溢出。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextHorzOverflowType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextHorzOverflowType (Text Horizontal Overflow Types)**

    This simple type specifies the text horizontal overflow types

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **clip** (Text Horizontal Overflow Enum ( Clip )) 
    
    :   When a big character does not fit into a line, clip it at the proper horizontal overflow.

    **overflow** (Text Horizontal Overflow Enum ( Overflow ))

    :   When a big character does not fit into a line, allow a horizontal overflow.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextHorzOverflowType) is located in §A.4.1. end note]

## 20.1.10.70 ST_TextIndent (文本缩进)

=== "中文"

    这个简单类型指定要使用的文本缩进量。

    此处使用的度量单位是EMU。
    
    这个简单类型的内容是 ST_Coordinate32Unqualified 数据类型（§20.1.10.18）的限制。
    
    此简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于-51206400。
    - 该简单类型的最大值小于或等于51206400。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextIndent) is located in §A.4.1. end note]

=== "英文"

    **ST_TextIndent (Text Indentation)**

    This simple type specifies the text indentation amount to be used.

    The units of measurement used here are EMUs (English Metric Units).

    This simple type's contents are a restriction of the ST_Coordinate32Unqualified datatype (§20.1.10.18).

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to -51206400.
    - This simple type has a maximum value of less than or equal to 51206400.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextIndent) is located in §A.4.1. end note]

## 20.1.10.71 ST_TextIndentLevelType (文本缩进级别类型)

=== "中文"

    这个简单类型指定缩进级别类型。我们支持列表级别从0到8，并使用-1和-2表示仅应存在于内存中的大纲模式级别。

    这个简单类型的内容是W3C XML Schema int数据类型的限制。
    
    此简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于0。
    - 该简单类型的最大值小于或等于8。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextIndentLevelType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextIndentLevelType (Text Indent Level Type)**

    This simple type specifies the indent level type. We support list level 0 to 8, and we use -1 and -2 for outline mode levels that should only exist in memory.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 8.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextIndentLevelType) is located in §A.4.1. end note]

## 20.1.10.72 ST_TextMargin (文本(外)边距)

=== "中文"

    这个简单类型指定了要使用的边距及其相应的大小。

    这个简单类型的内容是 ST_Coordinate32Unqualified 数据类型（§20.1.10.18）的限制。
    
    此简单类型还指定了以下限制：
    
    - 该简单类型的最小值大于或等于0。
    - 该简单类型的最大值小于或等于51206400。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextMargin) is located in §A.4.1. end note]

=== "英文"

    **ST_TextMargin (Text Margin)**

    This simple type specifies the margin that is used and its corresponding size.

    This simple type's contents are a restriction of the ST_Coordinate32Unqualified datatype (§20.1.10.18).

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 51206400.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextMargin) is located in §A.4.1. end note]

## 20.1.10.73 ST_TextNonNegativePoint (文本非负字体大小)

=== "中文"

    这个简单类型指定了以点的百分之一为单位的非负字体大小。它的取值范围是[0, 400000]。这个简单类型的内容是对W3C XML Schema int数据类型的限制。此外，它还指定了以下限制：

    - 最小值大于或等于0。
    - 最大值小于或等于400000。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextNonNegativePoint) is located in §A.4.1. end note]

=== "英文"

    **ST_TextNonNegativePoint (Text Non-Negative Point)**

    This simple type specifies a non-negative font size in hundredths of a point. This is restricted to the range [0, 400000].

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 400000.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextNonNegativePoint) is located in §A.4.1. end note]

## 20.1.10.74 ST_TextPoint (文档座标点)

=== "中文"

    这个简单类型指定了文档中的坐标。它可以用于测量或间距；其最大尺寸为+/- 4000点。

    它的内容可以包含以下内容之一：

    - 整数，其内容包括以点的百分之一为单位的测量值
    - 数字后面紧跟单位标识符

    这个简单类型是以下类型的并集：

    - ST_TextPointUnqualified 简单类型（§20.1.10.75）。
    - ST_UniversalMeasure 简单类型（§22.9.2.15）。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextPoint) is located in §A.4.1. end note]

=== "英文"

    **ST_TextPoint (Text Point)**

    This simple type specifies a coordinate within the document. This can be used for measurements or spacing; its maximum size is +/- 4000 points.

    Its contents can contain either:

    - A whole number, whose contents consist of a measurement in hundredths of a point
    - A number immediately followed by a unit identifier

    This simple type is a union of the following types:

    - The ST_TextPointUnqualified simple type (§20.1.10.75).
    - The ST_UniversalMeasure simple type (§22.9.2.15).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextPoint) is located in §A.4.1. end note]

## 20.1.10.75 ST_TextPointUnqualified (文本字号点数)

=== "中文"

    这种简单类型指定了字号的点数的百分之一。取值范围限定在[-400000, 400000]之间，即从-4000磅到4000磅。

    这种简单类型的内容是对W3C XML Schema int数据类型的限制。

    这种简单类型还指定了以下限制：

    - 最小值大于或等于-400000。
    - 最大值小于或等于400000。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextPointUnqualified) is located in §A.4.1. end note]

=== "英文"

    **ST_TextPointUnqualified (Text Point)**

    This simple type specifies a font size in hundredths of a point. This is restricted to the range [-400000, 400000], i.e from -4000 pt to 4000 pt.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to -400000.
    - This simple type has a maximum value of less than or equal to 400000.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextPointUnqualified) is located in §A.4.1. end note]

## 20.1.10.76 ST_TextShapeType (预置文本形状类型)

=== "中文"

    !!! info "译注"

        pdf 文档有图片样例

    这种简单类型指定了要用于形状的预设文本形状几何图形。使用此简单类型的枚举，可以自动生成构造自定义几何图形，而无需指定自定义几何图形。对于列出的每个枚举，还有相应的DrawingML代码，用于构造此形状的自定义几何图形。在每个预设文本形状的构造代码中，生成应用程序应始终保留用于计算目的的预定义指南。必要的指南应具有以下值。公式语法组件在gd元素（§20.1.9.11）的 `fmla` 属性中定义。
    
    **3/4 圆 ('3cd4') - 常量值为 "16200000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 270 度。
    
    **3/8 圆 ('3cd8') - 常量值为 "8100000.0"**

    :   此处的单位是 60,000 分之一度。这相当于 135 度。
    
    **5/8 圆 ('5cd8') - 常量值为 "13500000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 225 度。
    
    **7/8 圆 ('7cd8') - 常量值为 "18900000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 315 度。
    
    **形状底边 ('b') - 常量值为 "h"**
    
    :   这是形状的底边，由于形状的顶边被认为是0点，底边因此是形状的高度。
    
    **1/2 圆 ('cd2') - 常量值为 "10800000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 180 度。
    
    **1/4 圆 ('cd4') - 常量值为 "5400000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 90 度。
    
    **1/8 圆 ('cd8') - 常量值为 "2700000.0"**
    
    :   此处的单位是 60,000 分之一度。这相当于 45 度。
    
    **形状高度 ('h')**
    
    :   这是形状属性中定义的形状的可变高度。此值来自 `<spPr>` 元素中列出的形状变换。
    
    **水平中心 ('hc') - 计算值为 "*/ w 1.0 2.0"**

    :   这是形状的水平中心，即宽度除以2。
    
    **形状高度的1/2 ('hd2') - 计算值为 "*/ h 1.0 2.0"**
    
    :   这是形状高度的1/2。
    
    **形状高度的1/3 ('hd3') - 计算值为 "*/ h 1.0 3.0"**
    
    :   这是形状高度的1/3。
    
    **形状高度的1/4 ('hd4') - 计算值为 "*/ h 1.0 4.0"**
    
    :   这是形状高度的1/4。
    
    **形状高度的1/5 ('hd5') - 计算值为 "*/ h 1.0 5.0"**
    
    :   这是形状高度的1/5。
    
    **形状高度的1/6 ('hd6') - 计算值为 "*/ h 1.0 6.0"**
    
    :   这是形状高度的1/6。
    
    **形状高度的1/8 ('hd8') - 计算值为 "*/ h 1.0 8.0"**
    
    :   这是形状高度的1/8。
    
    **形状左边 ('l') - 常量值为 "0"**
    
    :   这是形状的左边缘，形状的左边缘被认为是水平0点。
    
    **形状最长边 ('ls') - 计算值为 "max w h"**
    
    :   这是形状的最长边。该值是宽度或高度，取决于哪个更大。
    
    **形状右边 ('r') - 常量值为 "w"**
    
    :   这是形状的右边缘，由于形状的左边缘被认为是0点，右边缘因此是形状的宽度。
    
    **形状的最短边 ('ss') - 计算值为 "min w h"**

    :   这是形状的最短边。该值是宽度或高度，取决于哪个更小。
    
    **形状最短边的1/2 ('ssd2') - 计算值为 "*/ ss 1.0 2.0"**
    
    :   这是形状最短边的1/2。
    
    **形状最短边的1/4 ('ssd4') - 计算值为 "*/ ss 1.0 4.0"**
    
    :   这是形状最短边的1/4。
    
    **形状最短边的1/6 ('ssd6') - 计算值为 "*/ ss 1.0 6.0"**
    
    :   这是形状最短边的1/6。
    
    **形状最短边的1/8 ('ssd8') - 计算值为 "*/ ss 1.0 8.0"**
    
    :   这是形状最短边的1/8。
    
    **形状最短边的1/16 ('ssd16') - 计算值为 "*/ ss 1.0 16.0"**
    
    :   这是形状最短边的1/16。
    
    **形状最短边的1/32 ('ssd32') - 计算值为 "*/ ss 1.0 32.0"**
    
    :   这是形状最短边的1/32。
    
    **形状上边 ('t') - 常量值为 "0"**
    
    :   这是形状的上边缘，形状的上边缘被认为是垂直0点。
    
    **形状的垂直中心 ('vc') - 计算值为 "*/ h 1.0 2.0"**
    
    :   这是形状的垂直中心，即高度除以2。
    
    **形状宽度 ('w')**
    
    :   这是形状的可变宽度，定义在形状属性中。此值来自`<spPr>`元素中列出的形状变换。

    **形状宽度的1/2 ('wd2') - 计算值为 "*/ w 1.0 2.0"**

    :   这是形状宽度的1/2。
    
    **形状宽度的1/3 ('wd3') - 计算值为 "*/ w 1.0 3.0"**
    
    :   这是形状宽度的1/3。
    
    **形状宽度的1/4 ('wd4') - 计算值为 "*/ w 1.0 4.0"**
    
    :   这是形状宽度的1/4。
    
    **形状宽度的1/5 ('wd5') - 计算值为 "*/ w 1.0 5.0"**
    
    :   这是形状宽度的1/5。
    
    **形状宽度的1/6 ('wd6') - 计算值为 "*/ w 1.0 6.0"**
    
    :   这是形状宽度的1/6。
    
    **形状宽度的1/8 ('wd8') - 计算值为 "*/ w 1.0 8.0"**
    
    :   这是形状宽度的1/8。
    
    **形状宽度的1/10 ('wd10') - 计算值为 "*/ w 1.0 10.0"**
    
    :   这是形状宽度的1/10。

    这个简单类型的内容是对W3C XML Schema标记数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的数值。

    ??? abstract "Enumeration"

        **textArchDown (下拱形文本形状 / Downward Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            指定一个文本形状，应与上面显示的规范形状相匹配。
            
            【注：可用于实现此效果的DrawingML标记的示例包含在附件D的预设文本弯曲电子附录的textArchDown元素中。该标记中使用的常数是上面更详细描述的指南。结束注】

        **textArchDownPour (向下倾倒拱形文本形状 / Downward Pour Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchDownPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textArchUp (向上拱形文字形状 / Upward Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textArchUpPour (向上倾倒拱形文字形状 / Upward Pour Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchUpPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textButton (Button Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textButton element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textButtonPour (Button Pour Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textButtonPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCanDown (Downward Can Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCanDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCanUp (Upward Can Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCanUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCascadeDown (Downward Cascade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCascadeDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCascadeUp (Upward Cascade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCascadeUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textChevron (Chevron Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textChevron element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textChevronInverted (Inverted Chevron Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textChevronInverted element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCircle (Circle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCircle element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCirclePour (Circle Pour Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCirclePour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCurveDown (Downward Curve Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCurveDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCurveUp (Upward Curve Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCurveUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflate (Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateBottom (Bottom Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateBottom element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateInflate (Deflate-Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateInflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateInflateDeflate (Deflate-Inflate-Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateInflateDeflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateTop (Top Deflate Text Shape) **

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateTop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDoubleWave1 (Double Wave 1 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDoubleWave1 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeDown (Downward Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeLeft (Left Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeLeft element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeRight (Right Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeRight element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeUp (Upward Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflate (Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflateBottom (Bottom Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflateBottom element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflateTop (Top Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflateTop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textNoShape (No Text Shape)**

        :   Specifies that the text has no associated shape with it and thus the text should not be warped but instead be constrained by the normal text bounding box.

        **textPlain (Plain Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textPlain element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textRingInside (Inside Ring Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textRingInside element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textRingOutside (Outside Ring Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textRingOutside element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textSlantDown (Downward Slant Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textSlantDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textSlantUp (Upward Slant Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textSlantUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textStop (Stop Sign Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textStop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textTriangle (Triangle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textTriangle element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textTriangleInverted (Inverted Triangle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textTriangleInverted element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave1 (Wave 1 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave1 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave2 (Wave 2 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave2 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave4 (Wave 4 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave4 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextShapeType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextShapeType (Preset Text Shape Types)**

    !!! info "译注"

        pdf 文档有图片样例

    This simple type specifies the preset text shape geometry that is to be used for a shape. An enumeration of this simple type is used so that a custom geometry does not have to be specified but instead can be constructed automatically by the generating application. For each enumeration listed there is also the corresponding DrawingML code that would be used to construct this shape were it a custom geometry. Within the construction code for each of these preset text shapes there are predefined guides that the generating application shall maintain for calculation purposes at all times. The necessary guides should have the following values. Formula syntax components are defined in the fmla attribute of the gd element (§20.1.9.11).
    
    **3/4 of a Circle ('3cd4') - Constant value of "16200000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 270 degrees.
    
    **3/8 of a Circle ('3cd8') - Constant value of "8100000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 135 degrees.
    
    **5/8 of a Circle ('5cd8') - Constant value of "13500000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 225 degrees.
    
    **7/8 of a Circle ('7cd8') - Constant value of "18900000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 315 degrees.
    
    **Shape Bottom Edge ('b') - Constant value of "h"**
    
    :   This is the bottom edge of the shape and since the top edge of the shape is considered the 0 point, the bottom edge is thus the shape height.
    
    **1/2 of a Circle ('cd2') - Constant value of "10800000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 180 degrees.
    
    **1/4 of a Circle ('cd4') - Constant value of "5400000.0"**
    
    :   The units here are in 60,000ths of a degree. This is equivalent to 90 degrees.
    
    **1/8 of a Circle ('cd8') - Constant value of "2700000.0"**

    :   The units here are in 60,000ths of a degree. This is equivalent to 45 degrees.
    
    **Shape Height ('h')**
    
    :   This is the variable height of the shape defined in the shape properties. This value is received from the shape transform listed within the `<spPr>` element.
    
    **Horizontal Center ('hc') - Calculated value of "*/ w 1.0 2.0"**

    :   This is the horizontal center of the shape which is just the width divided by 2.
    
    **1/2 of Shape Height ('hd2') - Calculated value of "*/ h 1.0 2.0"**
    
    :   This is 1/2 the shape height.
    
    **1/3 of Shape Height ('hd3') - Calculated value of "*/ h 1.0 3.0"**
    
    :   This is 1/3 the shape height.
    
    **1/4 of Shape Height ('hd4') - Calculated value of "*/ h 1.0 4.0"**
    
    :   This is 1/4 the shape height.
    
    **1/5 of Shape Height ('hd5') - Calculated value of "*/ h 1.0 5.0"**

    :   This is 1/5 the shape height.
    
    **1/6 of Shape Height ('hd6') - Calculated value of "*/ h 1.0 6.0"**
    
    :   This is 1/6 the shape height.
    
    **1/8 of Shape Height ('hd8') - Calculated value of "*/ h 1.0 8.0"**
    
    :   This is 1/8 the shape height.
    
    **Shape Left Edge ('l') - Constant value of "0"**
    
    :   This is the left edge of the shape and the left edge of the shape is considered the horizontal 0 point.
    
    **Longest Side of Shape ('ls') - Calculated value of "max w h"**
    
    :   This is the longest side of the shape. This value is either the width or the height depending on which is greater.
    
    **Shape Right Edge ('r') - Constant value of "w"**

    :   This is the right edge of the shape and since the left edge of the shape is considered the 0 point, the right edge is thus the shape width.
    
    **Shortest Side of Shape ('ss') - Calculated value of "min w h"**
    
    :   This is the shortest side of the shape. This value is either the width or the height depending on which is smaller.

    **1/2 Shortest Side of Shape ('ssd2') - Calculated value of "*/ ss 1.0 2.0"**
    
    :   This is 1/2 the shortest side of the shape.
    
    **1/4 Shortest Side of Shape ('ssd4') - Calculated value of "*/ ss 1.0 4.0"**
    
    :   This is 1/4 the shortest side of the shape.
    
    **1/6 Shortest Side of Shape ('ssd6') - Calculated value of "*/ ss 1.0 6.0"**
    
    :   This is 1/6 the shortest side of the shape.
    
    **1/8 Shortest Side of Shape ('ssd8') - Calculated value of "*/ ss 1.0 8.0"**
    
    :   This is 1/8 the shortest side of the shape.
    
    **1/16 Shortest Side of Shape ('ssd16') - Calculated value of "*/ ss 1.0 16.0"**
    
    :   This is 1/16 the shortest side of the shape.
    
    **1/32 Shortest Side of Shape ('ssd32') - Calculated value of "*/ ss 1.0 32.0"**
    
    :   This is 1/32 the shortest side of the shape.
    
    **Shape Top Edge ('t') - Constant value of "0"**
    
    :   This is the top edge of the shape and the top edge of the shape is considered the vertical 0 point.
    
    **Vertical Center of Shape ('vc') - Calculated value of "*/ h 1.0 2.0"**
    
    :   This is the vertical center of the shape which is just the height divided by 2. 
    
    **Shape Width ('w')**

    :   This is the variable width of the shape defined in the shape properties. This value is received from the shape transform listed within the `<spPr>` element.

    **1/2 of Shape Width ('wd2') - Calculated value of "*/ w 1.0 2.0"**

    :   This is 1/2 the shape width.

    **1/3 of Shape Width ('wd3') - Calculated value of "*/ w 1.0 3.0"**
    
    :   This is 1/3 the shape width.
    
    **1/4 of Shape Width ('wd4') - Calculated value of "*/ w 1.0 4.0"**
    
    :   This is 1/4 the shape width.
    
    **1/5 of Shape Width ('wd5') - Calculated value of "*/ w 1.0 5.0"**
    
    :   This is 1/5 the shape width.
    
    **1/6 of Shape Width ('wd6') - Calculated value of "*/ w 1.0 6.0"**
    
    :   This is 1/6 the shape width.
    
    **1/8 of Shape Width ('wd8') - Calculated value of "*/ w 1.0 8.0"**
    
    :   This is 1/8 the shape width.
    
    **1/10 of Shape Width ('wd10') - Calculated value of "*/ w 1.0 10.0"**
    
    :   This is 1/10 the shape width.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        **textArchDown (Downward Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textArchDownPour (Downward Pour Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchDownPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textArchUp (Upward Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textArchUpPour (Upward Pour Arch Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textArchUpPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textButton (Button Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textButton element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textButtonPour (Button Pour Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textButtonPour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCanDown (Downward Can Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCanDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCanUp (Upward Can Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCanUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCascadeDown (Downward Cascade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCascadeDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCascadeUp (Upward Cascade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCascadeUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textChevron (Chevron Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textChevron element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textChevronInverted (Inverted Chevron Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textChevronInverted element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCircle (Circle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCircle element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCirclePour (Circle Pour Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCirclePour element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCurveDown (Downward Curve Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCurveDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textCurveUp (Upward Curve Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textCurveUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflate (Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateBottom (Bottom Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateBottom element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateInflate (Deflate-Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateInflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateInflateDeflate (Deflate-Inflate-Deflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateInflateDeflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDeflateTop (Top Deflate Text Shape) **

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDeflateTop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textDoubleWave1 (Double Wave 1 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textDoubleWave1 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeDown (Downward Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeLeft (Left Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeLeft element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeRight (Right Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeRight element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textFadeUp (Upward Fade Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textFadeUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflate (Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflate element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflateBottom (Bottom Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflateBottom element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textInflateTop (Top Inflate Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textInflateTop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textNoShape (No Text Shape)**

        :   Specifies that the text has no associated shape with it and thus the text should not be warped but instead be constrained by the normal text bounding box.

        **textPlain (Plain Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textPlain element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textRingInside (Inside Ring Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textRingInside element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textRingOutside (Outside Ring Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textRingOutside element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textSlantDown (Downward Slant Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textSlantDown element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textSlantUp (Upward Slant Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textSlantUp element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textStop (Stop Sign Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textStop element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textTriangle (Triangle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textTriangle element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textTriangleInverted (Inverted Triangle Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textTriangleInverted element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave1 (Wave 1 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave1 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave2 (Wave 2 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave2 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        **textWave4 (Wave 4 Text Shape)**

        :   ![123](./imgs/aaa.png)
        
            Specifies a text shape that shall match the normative shape shown above.
        
            [Note: An example of DrawingML markup which can be used to achieve this effect is contained in the textWave4 element in the preset text warp electronic addenda of Annex D. The constants used in that markup are guides that are described in further detail above. end note]

        [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextShapeType) is located in §A.4.1. end note]

## 20.1.10.77 ST_TextSpacingPercentOrPercentString (文本字体间距百分比)

=== "中文"

    这个简单类型指定其内容将包含文本字体间距百分比。有关详细信息，请参阅联合体的成员类型。

    这个简单类型是以下类型的联合体：

    - ST_Percentage简单类型(§22.9.2.9)。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextSpacingPercentOrPercentString) is located in §A.4.1. end note]

=== "英文"

    **ST_TextSpacingPercentOrPercentString (Text Spacing Percent)**

    This simple type specifies that its contents will contain a text font spacing percentage. See the union's member types for details.

    This simple type is a union of the following types:

    - The ST_Percentage simple type (§22.9.2.9).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextSpacingPercentOrPercentString) is located in §A.4.1. end note]

## 20.1.10.78 ST_TextSpacingPoint (文本字体间距点)

=== "中文"

    这种简单类型指定了以字体点大小为单位使用的文本间距。

    这种简单类型的内容是对W3C XML Schema int数据类型的限制。
    
    这种简单类型还指定了以下限制：

    - 这种简单类型的最小值大于或等于0。
    - 这种简单类型的最大值小于或等于158400。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextSpacingPoint) is located in §A.4.1. end note]

=== "英文"

    **ST_TextSpacingPoint (Text Spacing Point)**

    This simple type specifies the Text Spacing that is used in terms of font point size.

    This simple type's contents are a restriction of the W3C XML Schema int datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 0.
    - This simple type has a maximum value of less than or equal to 158400.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextSpacingPoint) is located in §A.4.1. end note]

## 20.1.10.79 ST_TextStrikeType (文本删除线类型)

=== "中文"

    这个简单类型指定了删除线类型。

    这个简单类型的内容是对W3C XML Schema token数据类型的限制。

    这个简单类型被限制为以下表中列出的值：

    - **dblStrike**（文本删除线枚举（双删除线））：文本上应用了双删除线
    - **noStrike**（文本删除线枚举（无删除线））：文本上没有应用删除线
    - **sngStrike**（文本删除线枚举（单删除线））：文本上应用了单删除线

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextStrikeType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextStrikeType (Text Strike Type)**

    This simple type specifies the strike type.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    - **dblStrike** (Text Strike Enum ( Double Strike )):  A double strikethrough applied on the text
    - **noStrike** (Text Strike Enum ( No Strike )): No strike is applied to the text
    - **sngStrike** (Text Strike Enum ( Single Strike )): A single strikethrough is applied to the text

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextStrikeType) is located in §A.4.1. end note]

## 20.1.10.80 ST_TextTabAlignType (文本制表符对齐类型)

=== "中文"

    这个简单类型指定了文本制表符对齐类型。

    这个简单类型的内容是对W3C XML Schema令牌数据类型的限制。
    
    这个简单类型被限制为以下表中列出的值：
    
    **ctr**（文本制表符对齐枚举（居中））
    
    :   这个制表位上的文本是居中对齐的。
    
    **dec**（文本制表符对齐枚举（小数））
    
    :   在这个制表位上，小数点对齐。从用户的角度来看，这里的文本行为类似于右对齐，直到小数点，然后在小数点后就是左对齐。
    
    **l**（文本制表符对齐枚举（左））
    
    :   这个制表位上的文本是左对齐的。
    
    **r**（文本制表符对齐枚举（右））
    
    :   这个制表位上的文本是右对齐的。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextTabAlignType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextTabAlignType (Text Tab Alignment Types)**

    This simple type specifies the text tab alignment types.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **Enumeration**

    **ctr** (Text Tab Alignment Enum ( Center )) 
    
    :   The text at this tab stop is center aligned.
    
    **dec** (Text Tab Alignment Enum ( Decimal )) 
    
    :   At this tab stop, the decimals are lined up. From a user's point of view, the text here behaves as right aligned until the decimal, and then as left aligned after the decimal.

    **l** (Text Tab Alignment Enum ( Left)) 
    
    :   The text at this tab stop is left aligned.

    **r** (Text Tab Alignment Enum ( Right )) 
    
    :   The text at this tab stop is right aligned.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextTabAlignType) is located in §A.4.1. end note]

## 20.1.10.81 ST_TextTypeface (文本字体字形(typeface))

=== "中文"

    这个简单类型指定了我们表示字体字形的方式。
    
    这个简单类型的内容是对W3C XML Schema字符串数据类型的限制。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextTypeface) is located in §A.4.1. end note]

=== "英文"

    **ST_TextTypeface (Text Typeface)**

    This simple type specifies the way we represent a font typeface.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextTypeface) is located in §A.4.1. end note]

## 20.1.10.82 ST_TextUnderlineType (文本下划线类型)

=== "中文"

    这个简单类型指定了所使用的文本下划线类型。

    这个简单类型的内容是对W3C XML Schema令牌数据类型的限制。
    
    这个简单类型被限制为以下表中列出的值：
    
    **dash**（文本下划线枚举（虚线））
    
    :   用普通粗细的单虚线为文本加下划线。
    
    **dashHeavy**（文本下划线枚举（粗虚线））
    
    :   用粗虚线为文本加下划线。
    
    **dashLong**（文本下划线枚举（长虚线））
    
    :   用普通粗细的长虚线为文本加下划线。
    
    **dashLongHeavy**（文本下划线枚举（粗长虚线））
    
    :   用粗长虚线为文本加下划线。
    
    **dbl**（文本下划线枚举（双线））
    
    :   用普通粗细的双线为文本加下划线。
    
    **dotDash**（文本下划线枚举（点虚线））
    
    :   用由点和虚线重复组成的普通粗细线为文本加下划线。
    
    **dotDashHeavy**（文本下划线枚举（粗点虚线））
    
    :   用由点和虚线重复组成的粗线为文本加下划线。
    
    **dotDotDash**（文本下划线枚举（双点虚线））
    
    :   用由两个点和虚线重复组成的普通粗细线为文本加下划线。
    
    **dotDotDashHeavy**（文本下划线枚举（粗双点虚线））
    
    :   用由两个点和虚线重复组成的粗线为文本加下划线。
    
    **dotted**（文本下划线枚举（点线））
    
    :   用普通粗细的点线为文本加下划线。
    
    **dottedHeavy**（文本下划线枚举（粗点线））
    
    :   用粗点线为文本加下划线。
    
    **heavy**（文本下划线枚举（粗线））
    
    :   用粗线为文本加下划线。
    
    **none**（文本下划线枚举（无））
    
    :   我们不能暗示没有下划线是下划线未指定的情况，因为未指定意味着从特定样式派生，用户可能想要覆盖这一点，使一些文本不加下划线，即使样式另有规定。
    
    **sng**（文本下划线枚举（单线））
    
    :   用普通粗细的单线为文本加下划线。
    
    **wavy**（文本下划线枚举（波浪线））
    
    :   用普通粗细的波浪线为文本加下划线。
    
    **wavyDbl**（文本下划线枚举（双波浪线））
    
    :   用普通粗细的双波浪线为文本加下划线。
    
    **wavyHeavy**（文本下划线枚举（粗波浪线））
    
    :   用粗波浪线为文本加下划线。
    
    **words**（文本下划线枚举（单词））
    
    :   只为单词加下划线，而不包括它们之间的空格。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextUnderlineType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextUnderlineType (Text Underline Types)**

    This simple type specifies the text underline types that is used.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **dash** (Text Underline Enum ( Dashed ))

    :   Underline the text with a single, dashed line of normal thickness.

    **dashHeavy** (Text Underline Enum ( Heavy Dashed )) 

    :   Underline the text with a single, dashed, thick line.

    **dashLong** (Text Underline Enum ( Long Dashed )) 

    :   Underline the text with a single line consisting of long dashes of normal thickness.

    **dashLongHeavy** (Text Underline Enum ( Heavy Long Dashed ))

    :   Underline the text with a single line consisting of long, thick dashes.

    **dbl** (Text Underline Enum ( Double )) 
    
    :   Underline the text with two lines of normal thickness.

    **dotDash** (Text Underline Enum ( Dot Dash )) 
    
    :   Underline the text with a single line of normal thickness consisting of repeating dots and dashes.

    **dotDashHeavy** (Text Underline Enum ( Heavy Dot Dash ))

    :   Underline the text with a single, thick line consisting of repeating dots and dashes.

    **dotDotDash** (Text Underline Enum ( Dot Dot Dash )) 

    :   Underline the text with a single line of normal thickness consisting of repeating two dots and dashes.

    **dotDotDashHeavy** (Text Underline Enum ( Heavy Dot Dot Dash ))

    :   Underline the text with a single, thick line consisting of repeating two dots and dashes.

    **dotted** (Text Underline Enum ( Dotted )) 
    
    :   Underline the text with a single, dotted line of normal thickness.

    **dottedHeavy** (Text Underline Enum ( Heavy Dotted )) 
    
    :   Underline the text with a single, thick, dotted line.

    **heavy** (Text Underline Enum ( Heavy )) 
    
    :   Underline the text with a single, thick line.

    **none** (Text Underline Enum ( None )) 
    
    :   The reason we cannot implicitly have noUnderline be the scenario where underline is not specified is because not being specified implies deriving from a particular style and the user might want to override that and make some text not be underlined even though the style says otherwise.

    **sng** (Text Underline Enum ( Single )) 
    
    :   Underline the text with a single line of normal thickness.

    **wavy** (Text Underline Enum ( Wavy )) 
    
    :   Underline the text with a single wavy line of normal thickness.

    **wavyDbl** (Text Underline Enum ( Double Wavy )) 
    
    :   Underline the text with two wavy lines of normal thickness.

    **wavyHeavy** (Text Underline Enum ( Heavy Wavy )) 
    
    :   Underline the text with a single, thick wavy line.

    **words** (Text Underline Enum ( Words )) 
    
    :   Underline just the words and not the spaces between them.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextUnderlineType) is located in §A.4.1. end note]

## 20.1.10.83 ST_TextVerticalType (垂直文本类型)

=== "中文"

    如果存在垂直文本，确定将使用哪种类型的垂直文本。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    - **eaVert** (垂直文本类型枚举（东亚垂直）)
    
        :   垂直文本的特殊版本，其中一些字体显示为沿90度旋转，而另一些字体（主要是东亚字体）显示为垂直。
    
    - **horz** (垂直文本类型枚举（水平）)
    
        :   水平文本。这应该是默认值。
    
    - **mongolianVert** (垂直文本类型枚举（蒙古垂直）)
    
        :   垂直文本的特殊版本，其中一些字体显示为沿90度旋转，而另一些字体（主要是东亚字体）以垂直方式显示。与eastAsianVertical的区别在于文本从上到下然后从左到右流动，而不是从右到左。
    
    - **vert** (垂直文本类型枚举（垂直）)
    
        :   确定是否所有文本都是垂直方向的（每行顺时针旋转90度，所以从上到下; 每一行都在前一行的左侧）。
    
    - **vert270** (垂直文本类型枚举（垂直270）)
    
        :   确定是否所有文本都是垂直方向的（每行顺时针旋转270度，所以从下到上; 每一行都在前一行的右侧）。
    
    - **wordArtVert** (垂直文本类型枚举（WordArt垂直）)
    
        :   确定是否所有文本都是垂直的（"一个字母在另一个字母的上面"）。
    
    - **wordArtVertRtl** (垂直WordArt从右到左)
    
        :   指定应该从右到左而不是从左到右显示垂直WordArt。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextVerticalType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextVerticalType (Vertical Text Types)**

    If there is vertical text, determines what kind of vertical text is going to be used.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **eaVert** (Vertical Text Type Enum ( East Asian Vertical )) 
    
    :   A special version of vertical text, where some fonts are displayed as if rotated by 90 degrees while some fonts (mostly East Asian) are displayed vertical.

    **horz** (Vertical Text Type Enum ( Horizontal )) 
    
    :   Horizontal text. This should be default.

    **mongolianVert** (Vertical Text Type Enum ( Mongolian Vertical )) 
    
    :   A special version of vertical text, where some fonts are displayed as if rotated by 90 degrees while some fonts (mostly East Asian) are displayed vertical. The difference between this and the eastAsianVertical is the text flows top down then LEFT RIGHT, instead of RIGHT LEFT

    **vert** (Vertical Text Type Enum ( Vertical )) 
    
    :   Determines if all of the text is vertical orientation (each line is 90 degrees rotated clockwise, so it goes from top to bottom; each next line is to the left from the previous one).

    **vert270** (Vertical Text Type Enum ( Vertical 270 )) 
    
    :   Determines if all of the text is vertical orientation (each line is 270 degrees rotated clockwise, so it goes from bottom to top; each next line is to the right from the previous one).

    wordArtVert (Vertical Text Type Enum ( WordArtVertical ))

    :   Determines if all of the text is vertical ("one letter on top of another").

    wordArtVertRtl (Vertical WordArt Right to Left) 
    
    :   Specifies that vertical WordArt should be shown from right to left rather than left to right.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextVerticalType) is located in §A.4.1. end note]

## 20.1.10.84 ST_TextVertOverflowType (文本垂直溢出方式)

=== "中文"

    这个简单类型指定了文本的垂直溢出方式。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    **clip** (文本溢出枚举（剪切）)
    
        :   注意上下边界。不提供任何指示存在不可见文本的迹象。
    
    **ellipsis** (文本溢出枚举（省略号）)
    
        :   注意上下边界。使用省略号表示存在不可见文本。
    
    **overflow** (文本溢出枚举（溢出）)
    
        :   文本溢出，不注意上下边界。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextVertOverflowType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextVertOverflowType (Text Vertical Overflow)**

    This simple type specifies the text vertical overflow.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **clip** (Text Overflow Enum ( Clip )) 
    
    :   Pay attention to top and bottom barriers. Provide no indication that there is text which is not visible.
    
    **ellipsis** (Text Overflow Enum ( Ellipsis )) 
    
    :   Pay attention to top and bottom barriers. Use an ellipsis to denote that there is text which is not visible.
    
    **overflow** (Text Overflow Enum ( Overflow )) 
    
    :   Overflow the text and pay no attention to top and bottom barriers. 

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextVertOverflowType) is located in §A.4.1. end note]

## 20.1.10.85 ST_TextWrappingType (文本包裹/换行类型)

=== "中文"

    文本换行类型
    
    这个简单类型的内容是对W3C XML模式token数据类型的限制。
    
    这种简单类型被限制为以下表中列出的值：
    
    **none**（文本换行类型枚举（无））
    
    :   该文本体上没有换行。单词会溢出，而不考虑边界矩形。
    
    **square**（文本换行类型枚举（方形））
    
    :   决定是否在边界矩形内换行单词。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextWrappingType) is located in §A.4.1. end note]

=== "英文"

    **ST_TextWrappingType (Text Wrapping Types)**

    Text Wrapping Types

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **none** (Text Wrapping Type Enum ( None )) 
    
    :   No wrapping occurs on this text body. Words spill out without paying attention to the bounding rectangle boundaries.

    **square** (Text Wrapping Type Enum ( Square )) 
    
    :   Determines whether we wrap words within the bounding rectangle.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextWrappingType) is located in §A.4.1. end note]

## 20.1.10.86 ST_TileFlipMode (翻转平铺模式)

=== "中文"

    这个简单类型指示在使用它来填充较大的填充区域时是否以及如何翻转平铺区域的内容。

    这个简单类型的内容是对W3C XML模式token数据类型的限制。
    
    这个简单类型被限制为以下表格中列出的值：
    
    **none** (无)
    
    :   ![123](./imgs/aaa.png)
        
        平铺不翻转。
    
    **x** (水平)
    
    :   ![123](./imgs/aaa.png)
        
        平铺在水平方向翻转。
    
    **xy** (水平和垂直)
    
    :   ![123](./imgs/aaa.png)
        
        平铺在水平和垂直方向都翻转。
    
    **y** (垂直)
    
    :   ![123](./imgs/aaa.png)
        
        平铺在垂直方向翻转。

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TileFlipMode) is located in §A.4.1. end note]

=== "英文"

    **ST_TileFlipMode (Tile Flip Mode)**

    This simple type indicates whether/how to flip the contents of a tile region when using it to fill a larger fill region.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

    This simple type is restricted to the values listed in the following table:

    **none** (None)

    :   ![123](./imgs/aaa.png)
        
        Tiles are not flipped.

    **x** (Horizontal)

    :   ![123](./imgs/aaa.png)
        
        Tiles are flipped horizontally.

    **xy** (Horizontal and Vertical)

    :   ![123](./imgs/aaa.png)
        
        Tiles are flipped both horizontally and vertically.

    **y** (Vertical)

    :   ![123](./imgs/aaa.png)
        
        Tiles are flipped vertically.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TileFlipMode) is located in §A.4.1. end note]

## 20.1.10.87 ST_TextBulletSize (文本项目符号百分比)

=== "中文"

    这个简单类型指定了项目符号百分比的范围。项目符号百分比是项目符号相对于接下来的文本的大小，最小大小为25%，最大大小为400%。

    这个简单类型是以下类型的并集：
    
    - ST_TextBulletSizePercent 简单类型 (§20.1.10.62)

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletSize) is located in § A.4.1. end note]

=== "英文"

    **ST_TextBulletSize (Bullet Size Percentage)**

    This simple type specifies the range that the bullet percent can be. A bullet percent is the size of the bullet with respect to the text that should follow it, with a minimum size of 25% and maximum size of 400%.

    This simple type is a union of the following types:

    - The ST_TextBulletSizePercent simple type (§20.1.10.62)

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TextBulletSize) is located in § A.4.1. end note]
