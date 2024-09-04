# 17.2 主文档故事

**Main Document Story**

=== "中文"

    根据[第4节](../chapter-4.md)的定义，WordprocessingML文档包含了类别为Wordprocessing的Office Open XML文档的标记。从语法上讲，该文档由两种信息的编译组成，这些信息被组合在一起以创建此版本：
    
    - 属性(Properties)[示例：样式、编号定义等]
    - 故事(Stories)[示例：主文档、注释、页眉等]
    
    在WordprocessingML中，故事(stories)是一个或多个由`p`元素([§17.3.1.22])的父元素定义的唯一容器。故事(stories)包含文档的内容。文档的属性应用于每个故事(stories)的内容以创建该版本。大部分WordprocessingML文档的内容位于主文档故事(story)中，该故事(story)存储在主文档部件的body元素内（[§11.3.10]）。
    
    [示例：考虑一个只有一个段落的主文档故事的文档。该文档在其主文档部件中需要以下WordprocessingML：
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    段落位于body元素内部，使其成为主文档故事的一部分。结束示例]

=== "英文"
    
    As defined in §4, a WordprocessingML document contains the markup for a rendition of an Office Open XML document of category Wordprocessing. Syntactically, the document consists of a compilation of two kinds of information, which are combined to create this rendition:
    
    - Properties [Example: styles, numbering definitions, etc. end example]
    - Stories [Example: main document, comments, headers, etc. end example]
    
    In WordprocessingML, stories are unique containers for one or more paragraphs, as defined by the parent elements of the p element ([§17.3.1.22]). Stories contain the document's content. The properties of the document are applied to the contents of each story to create the rendition. Most of the content in a WordprocessingML document is located in the main document story, which is stored inside the body element within the Main Document part ([§11.3.10]).
    
    [Example: Consider a document with a single paragraph in the main document story. This document would require the following WordprocessingML in its main document part:
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    The fact that the paragraph is inside the body element makes it part of the main document story. end example]


## 17.2.1 background (文档背景)

**background (Document Background)**

=== "中文"
    
    此元素指定包含背景元素的文档的每个页面的背景。文档的背景是整个页面表面的图像或填充，位于所有其他文档内容之后。
    
    背景元素的绘图(drawing)[§17.3.3.9]子元素允许将任何DrawingML效果应用于文档的背景。
    
    然而，对于纯色填充背景，此元素上的属性允许使用任何RGB或主题颜色值（后者是对文档主题部分的引用）。
    
    [示例：考虑一个使用从黑色到accent3主题颜色之间的渐变填充背景的文档，如下所示：
    
    ![123](./imgs/Image7260.jpg)
    
    此背景需要以下WordprocessingML标记：
    
    <w:background w:themeColor="accent3">
        <w:drawing>
            <wp:inline … >
                <a:graphic>
                    <a:graphicData … >
                        …
                    </a:graphicData>
                </a:graphic>
            </wp:inline>
        </w:drawing>
    </w:background>
    
    生成的背景由来自themeColor属性的accent3主题颜色的单色填充组成，位于gradientCenter填充下方。示例结束]
    
    ??? abstract "Attributes"
    
        **color**（背景颜色）
        
        :   指定文档背景的颜色。
        
            该值可以定义为以下两种形式之一：
            
            - 使用RGB颜色模型的颜色值，其红、绿和蓝值以0到255的数字编写，以十六进制编码并连接在一起。【示例：全强度红色将是255红、0绿、0蓝，编码为FF、00、00，并连接为FF0000。示例结束】。RGB颜色在sRGB颜色空间中指定。
            - auto，以便允许使用者自动确定背景颜色，以使文档的文本可读。【示例：具有白色文本和自动背景颜色的文档可能会使用黑色背景，以确保内容的可读性。示例结束】
            
            如果背景通过themeColor属性指定使用主题颜色，则忽略此值。【注意：应用程序不建议在同一父元素上同时指定color和themeColor属性。注释结束】
            
            如果既没有color属性也没有themeColor属性，则将处理父页面，就好像没有定义背景一样。
            
            【示例：考虑以下值为2C34FF的背景颜色：
            
            ```xml
            <w:background … w:color="2C34FF"/>
            ```
            
            因此，背景颜色是具有RGB值44、52、255（上述十六进制值的十进制解码）的颜色。示例结束】
            
            此属性的可能值由ST_HexColor简单类型（[§17.18.38]）定义。
    
        **themeColor**（背景主题颜色）
        
        :   指定用于生成背景颜色的基本主题颜色。背景颜色是与themeColor关联的RGB值，进一步通过themeTint或themeShade（如果存在）进行转换，否则背景颜色就是与themeColor关联的RGB值。
        
            指定的主题颜色是对文档主题部分（[§14.2.7]和[§20.1.6.9]）中预定义的主题颜色之一的引用，这允许在文档中集中设置颜色信息。
            
            如果指定了颜色属性，则将忽略其值，而使用该属性与任何适当的themeTint和themeShade属性值计算所产生的颜色。
            
            为了确定要显示的颜色，执行以下操作：
            
            - 使用ST_ThemeColor简单类型（[§17.18.97]）中指定的映射，读取clrSchemeMapping元素（[§17.15.1.20]）上的适当属性。
            - 使用该值和ST_ColorSchemeIndex简单类型（[§17.18.103]）中指定的映射，读取文档主题部分中的适当元素，以获取基本主题颜色。
            - 根据themeTint或themeShade属性的存在修改指定的颜色。
            
            [示例：考虑配置为使用accent5主题颜色的背景，导致以下WordprocessingML标记：
            
            ```xml
            <w:background w:themeColor="accent5" />
            ```
            
            如果设置部分包含以下标记：
            
            ```xml
            <w:clrSchemeMapping … w:accent5="accent5"/>
            ```
            
            和主题部分包含以下XML标记：
            
            ```xml
            <a:accent5>
                <a:srgbClr val="BCBCBC"/>
            </a:accent5>
            ```
            
            则生成的背景颜色将为BCBCBC。结束示例]
            
            此属性的可能值由ST_ThemeColor简单类型（[§17.18.97]）定义。
                
        **themeShade**（背景主题颜色阴影）
        
        :   指定应用于此背景的提供的主题颜色（如果有）的阴影值。如果未指定themeColor属性，则不应指定此属性。
            
            如果提供了themeShade，则将其应用于主题颜色（来自主题部分）的RGB值，以确定应用于此背景的最终颜色。
            
            如果提供了themeTint，则应忽略此属性的值。
            
            themeShade值存储为应用于当前背景的阴影值的十六进制编码（从0到255）。
            
            [示例：考虑在文档中应用了60％的阴影到背景上。该阴影计算如下：
            
            ```text
            𝑆𝑥𝑚𝑙 = 0.6 ∗ 255
                = 153
                = 99(十六进制)
            ```
            
            文件格式中生成的themeShade值将为99。结束示例]
            
            给定一个以RRGGBB格式定义的RGB颜色，阴影应用如下：
            
            - 将颜色转换为HSL颜色格式（值从0到1）
            - 根据以下方式修改亮度因子：
            
                L′ = L ∗ Shade<sub>percentage</sub>
            
            - 将结果HSL颜色转换为RGB
            
            [示例：考虑一个使用accent2主题颜色的背景的文档，其RGB值（以RRGGBB十六进制格式）为C0504D。
            
            等效的HSL颜色值为（1/360，0.48，0.53）。
            
            将阴影百分比设为75％应用于亮度后，我们得到：
            
            ```text
            𝐿′  = 0.53 ∗ 0.75
                = 0.39698
            ```
            
            将结果HSL颜色值（360，0.48，0.39698）转换回RGB，我们得到943634。
            
            这个转换后的值可以在结果背景的颜色属性中看到：
            
            ```xml
            <w:background w:color="943634" w:themeColor="accent2" w:themeShade="BF"/>
            ```
            
            结束示例]
            
            此属性的可能值由ST_UcharHexNumber简单类型（[§17.18.98]）定义。
    
        **themeTint**（背景主题颜色色调）
        
        :   指定应用于此背景的提供的主题颜色（如果有）的色调值。如果未指定themeColor属性，则不应指定此属性。
            
            如果提供了themeTint，则将其应用于主题颜色（来自主题部分）的RGB值，以确定应用于文档背景的最终颜色。
            
            themeTint值存储为应用于当前背景的色调值的十六进制编码（从0到255）。
            
            [示例：考虑在文档中应用了60％的色调到背景上。该色调计算如下：
            
            ```text
            𝑇𝑥𝑚𝑙 = 0.4 ∗ 255
                = 102
                = 66(十六进制)
            ```
            
            文件格式中生成的themeTint值将为66。结束示例]
            
            给定一个以RRGGBB格式定义的RGB颜色，色调应用如下：
            
            - 将颜色转换为HSL颜色格式（值从0到1）
            - 根据以下方式修改亮度因子：
            
                L′ = L ∗ Tint<sub>pct</sub> + (1 − Tint<sub>pct</sub> )
            
            - 将结果HSL颜色转换为RGB
            
            [示例：考虑一个使用accent2主题颜色的背景的文档，其RGB值（以RRGGBB十六进制格式）为4F81BD。
            
            等效的HSL颜色值为（213/360，0.45，0.53）。
            
            将色调百分比设为60％应用于亮度后，我们得到：
            
            ```text
            𝐿′ = 0.53 ∗ 0.6 + (1 − .6)
                = 0.71
            ```
            
            将结果HSL颜色值（213/360，0.45，0.71）转换回RGB，我们得到95B3D7。
            
            这个转换后的值可以在结果背景的颜色属性中看到：
            
            ```xml
            <w:background w:color="95B3D7" w:themeColor="accent2"
            w:themeTint="99"/>
            ```
            
            结束示例]
            
            此属性的可能值由ST_UcharHexNumber简单类型（[§17.18.98]）定义。
        
    [Note: The W3C XML Schema definition of this element’s content model (CT_Background) is located in §A.1. end note]

=== "英文"
    
    This element specifies the background for every page of the document containing the background element. A document's background is the image or fill for the entire page surface, behind all other document content.
    
    The drawing §17.3.3.9 child elements of the background element allows any DrawingML effect to be applied to the document's background.
    
    For solid color fill backgrounds, however, the attributes on this element allow the use of any RGB or theme color value (the latter a reference to the document's themes part).
    
    [Example: Consider a document which utilizes a gradient fill background moving between black and the accent3 theme color, as follows:
    
    ![123](./imgs/Image7260.jpg)
    
    This background would require the following WordprocessingML markup:
    
    <w:background w:themeColor="accent3">
        <w:drawing>
            <wp:inline … >
                <a:graphic>
                    <a:graphicData … >
                        …
                    </a:graphicData>
                </a:graphic>
            </wp:inline>
        </w:drawing>
    </w:background>
    
    The resulting background consists of a single color fill of the accent3 theme color from the themeColor attribute, layered under a gradientCenter fill. end example]
    
    ??? abstract "Attributes"
    
        **color** (Background Color)
    
        :   Specifies the color for the background of the document.
    
            This value can be defined as either:
            
            - A color value using the RGB color model whose red, green, and blue values are written as numbers in the range 0 to 255, hex encoded, and concatenated. [Example: Full intensity red would be 255 red, 0 green, 0 blue, encoded to FF, 00, 00, and concatenated to FF0000. end example]. RGB colors are specified in the sRGB color space.
            - auto to allow a consumer to automatically determine the background color in order to make the document's text readable. [Example: A document with white text and a background color of auto might result in the use of a black background, in order to ensure legibility of the content. end example]
            
            If the background specifies the use of a theme color via the themeColor attribute, this value is ignored. [Note: Applications are discouraged from specifying both the color and themeColor attributes on the same parent element. end note]
    
            If neither the color nor themeColor attributes are present, the parent page shall be treated as though it has no background defined.
            
            [Example: Consider a background color with value 2C34FF, as follows:
            
            ```xml
            <w:background … w:color="2C34FF"/>
            ```
            
            The background color is therefore the color with RGB value 44,52,255 (the decimal decoding of the hex value above). end example]
            
            The possible values for this attribute are defined by the ST_HexColor simple type ([§17.18.38]).
    
        **themeColor** (Background Theme Color)
    
        :   Specifies the base theme color used to generate the background color. The background color is the RGB value associated with themeColor as further transformed by themeTint or themeShade (if one is present), else the background color is the RGB value associated with themeColor.
    
            The specified theme color is a reference to one of the predefined theme colors, located in the document's Theme part ([§14.2.7] and [§20.1.6.9]), which allows color information to be set centrally in the document.
    
            If the color attribute is specified, its value shall be ignored in favor of the color resulting from the use of this attribute with any appropriate themeTint and themeShade attribute value calculations applied.
    
            To determine the color to display, the following actions are performed:
            
            - Using the mapping specified in the ST_ThemeColor simple type ([§17.18.97]), the appropriate attribute on the clrSchemeMapping element ([§17.15.1.20]) is read.
            - Using that value and the mapping specified in the ST_ColorSchemeIndex simple type ([§17.18.103]), the appropriate element in the document’s Theme part is read to get the base theme color.
            - The specified color is modified based on the presence of the themeTint or themeShade attribute.
            
            [Example: Consider a background configured to use the accent5 theme color, resulting in the following WordprocessingML markup:
            
            ```xml
            <w:background w:themeColor="accent5" />
            ```
            
            If the Settings part contained the following markup:
    
            ```xml
            <w:clrSchemeMapping … w:accent5="accent5"/>
            ```
            
            and the Theme part contained the following XML markup:
    
            ```xml
            <a:accent5>
                <a:srgbClr val="BCBCBC"/>
            </a:accent5>
            ```
    
            the resulting background color would be BCBCBC. end example]
            
            The possible values for this attribute are defined by the ST_ThemeColor simple type (§17.18.97).
        
        **themeShade** (Background Theme Color Shade)
    
        :   Specifies the shade value applied to the supplied theme color (if any) for this background. If the themeColor attribute is not specified, this attribute shall not be specified.
            
            If the themeShade is supplied, then it is applied to the RGB value of the theme color (from the theme part) to determine the final color applied to this background.
            
            If the themeTint is supplied, the value of this attribute shall be ignored.
            
            The themeShade value is stored as a hex encoding of the shade value (from 0–255) applied to the current background.
            
            [Example: Consider a shade of 60% applied to a background in a document. This shade is calculated as follows:
            
            ```text
            𝑆𝑥𝑚𝑙 = 0.6 ∗ 255
                = 153
                = 99(ℎ𝑒𝑥)
            ```
            
            The resulting themeShade value in the file format would be 99. end example]
            
            Given an RGB color defined as three hex values in RRGGBB format, the shade is applied as follows:
            
            - Convert the color to the HSL color format (values from 0 to 1)
            - Modify the luminance factor as follows:
                
                L′ = L ∗ Shade<sub>percentage</sub>
            
            - Convert the resultant HSL color to RGB
            
            [Example: Consider a document with a background using the accent2 theme color, whose RGB value (in RRGGBB hex format) is C0504D.
            
            The equivalent HSL color value would be (1/360, 0.48, 0.53).
            
            Applying the shade formula with a shade percentage of 75% to the luminance, we get:
            
            ```text
            𝐿′  = 0.53 ∗ 0.75
                = 0.39698
            ```
            
            Taking the resulting HSL color value of (360 , 0.48,0.39698)and converting back to RGB, we get 943634.
            
            This transformed value can be seen in the resulting background's color attribute:
            
            ```xml
            <w:background w:color="943634" w:themeColor="accent2" w:themeShade="BF"/>
            ```
            
            end example]
            
            The possible values for this attribute are defined by the ST_UcharHexNumber simple type ([§17.18.98]).
    
        **themeTint** (Background Theme Color Tint)
    
        :   Specifies the tint value applied to the supplied theme color (if any) for this background. If the themeColor attribute is not specified, this attribute shall not be specified.
    
            If the themeTint is supplied, then it is applied to the RGB value of the theme color (from the theme part) to determine the final color applied to the document's background.
            
            The themeTint value is stored as a hex encoding of the tint value (from 0–255) applied to the current background.
            
            [Example: Consider a tint of 60% applied to a background in a document. This tint is calculated as follows:
    
            ```text
            𝑇𝑥𝑚𝑙 = 0.4 ∗ 255
                = 102
                = 66(ℎ𝑒𝑥)
            ```
    
            The resulting themeTint value in the file format would be 66. end example]
    
            Given an RGB color defined as three hex values in RRGGBB format, the shade is applied as follows:
            
            - Convert the color to the HSL color format (values from 0 to 1)
            - Modify the luminance factor as follows:
            
                L′ = L ∗ Tint<sub>pct</sub> + (1 − Tint<sub>pct</sub> )
    
            - Convert the resultant HSL color to RGB
            
            [Example: Consider a document with a background using the accent2 theme color, whose RGB value (in RRGGBB hex format) is 4F81BD.
    
            The equivalent HSL color value would be (213/360 , 0.45,0.53).
            
            Applying the tint formula with a tint percentage of 60% to the luminance, we get:
    
            ```text
            𝐿′ = 0.53 ∗ 0.6 + (1 − .6)
               = 0.71
            ```
    
            Taking the resulting HSL color value of (213/360 , 0.45,0.71)and converting back to RGB, we get 95B3D7.
    
            This transformed value can be seen in the resulting background's color attribute:
    
            ```xml
            <w:background w:color="95B3D7" w:themeColor="accent2"
            w:themeTint="99"/>
            ```
    
            end example]
    
            The possible values for this attribute are defined by the ST_UcharHexNumber simple type (§17.18.98).
        
    [Note: The W3C XML Schema definition of this element’s content model (CT_Background) is located in §A.1. end note]

## 17.2.2 body (文档正文)

**body (Document Body)**

=== "中文"
    
    该元素指定文档主体的内容 - 即主文档编辑表面。

    文档主体包含所谓的块级标记 - 可以作为WordprocessingML文档中段落的同级元素存在的标记。
    
    [示例：考虑一个主文档故事中只有一个段落的文档。该文档在其主文档部件中需要以下WordprocessingML：
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    段落在body元素内部使其成为主文档故事的一部分。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Body) is located in §A.1. end note]

=== "英文"
    
    This element specifies the contents of the body of the document - the main document editing surface.
    
    The document body contains what is referred to as block-level markup - markup which can exist as a sibling element to paragraphs in a WordprocessingML document.
    
    [Example: Consider a document with a single paragraph in the main document story. This document would require the following WordprocessingML in its main document part:
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    The fact that the paragraph is inside the body element makes it part of the main document story. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Body) is located in §A.1. end note]


## 17.2.3 document (文档)

**document (Document)**

=== "中文"

    该元素指定WordprocessingML文档中主文档部分的内容。
    
    [示例：考虑一个基本WordprocessingML文档中主文档部分的基本结构如下：
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    主文档部分的所有内容都包含在document元素下。结束示例]
    
    ??? abstract "属性"
    
        **conformance**（文档符合类别）
    
        :   指定WordprocessingML文档符合的符合类别（[§2.1]）。
    
            如果省略此属性，则其默认值为transitional。
            
            [示例：考虑以下WordprocessingML主文档部分标记：
            
            ```xml
            <w:document w:conformance="strict">
            …
            </w:document>
            ```
            
            此文档具有strict的符合属性值，因此符合WML Strict符合类别。结束示例]
            
            此属性的可能值由ST_ConformanceClass简单类型（[§22.9.2.2]）定义。

    [Note: The W3C XML Schema definition of this element’s content model (CT_Document) is located in §A.1. end note]

=== "英文"

    This element specifies the contents of a main document part in a WordprocessingML document.

    [Example: Consider the basic structure of the main document part in a basic WordprocessingML document, as follows:
    
    ```xml
    <w:document>
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    All of the contents of the main document part are contained beneath the document element. end example]

    ??? abstract "Attributes"

        **conformance** (Document Conformance Class)

        :   Specifies the conformance class ([§2.1]) to which the WordprocessingML document conforms.

            If this attribute is omitted, its default value is transitional.
            
            [Example: Consider the following WordprocessingML Main Document part markup:
            
            ```xml
            <w:document w:conformance="strict">
            …
            </w:document>
            ```
            
            This document has a conformance attribute value of strict, therefore it conforms to the WML Strict conformance class. end example]
            
            The possible values for this attribute are defined by the ST_ConformanceClass simple type (§22.9.2.2).

    [Note: The W3C XML Schema definition of this element’s content model (CT_Document) is located in §A.1. end note]

[§2.1]: ../chapter-2.md#21-文档一致性
[§11.3.10]: ../chapter-11.md#11310-主文档部件
[§14.2.7]: ../chapter-14.md#1427-主题部件
[§17.3.1.22]: ./03paragraphs.md#173122-p-段落
[§17.3.3.9]: ./03paragraphs.md#17339-drawing-drawingml对象
[§17.15.1.20]: ./15settings.md#1715120-clrschememapping-主题颜色映射
[§17.18.38]: ./17miscellaneous.md#171838-st_hexcolor-色值
[§17.18.97]: ./17miscellaneous.md#171897-st_themecolor-主题颜色
[§17.18.98]: ./17miscellaneous.md#171898-st_ucharhexnumber-两位十六进制值
[§17.18.103]: ./17miscellaneous.md#1718103-st_wmlcolorschemeindex-主题颜色参考
[§20.1.6.9]: ../chapter20/main/shared_style_sheet.md#20169-theme-主题
[§22.9.2.2]: ../chapter22/sharedsimpletypes.md#22922-st_conformanceclass-文档一致性等级值

