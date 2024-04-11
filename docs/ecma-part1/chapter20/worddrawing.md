# 20.4 DrawingML - WordprocessingML Drawing

=== "中文"

    在 WordprocessingML 文档中，可以包含图形 DrawingML 对象：

    - Pictures ([§20.2])
    - Locked Canvases ([§20.3])
    - Diagrams ([§21.4])
    - Charts ([§21.2])
    
    当这些对象出现在文字处理文档中时，有必要包括指定这些对象相对于分页文档如何定位的信息。 [例如: 对象是否与文本对齐显示。 ]

    WordprocessingML Drawing 命名空间发挥此功能，指定在字处理文档中锚定和显示 DrawingML 对象所需的所有信息。

    !!! info "例如"
    
        考虑一张 DrawingML 图片，该图片必须显示在其出现的打印页面的中心，并根据需要修改文本流。 该对象将指定如下：

        ```xml
        <w:r>
            <w:drawing>
                <wp:anchor relativeHeight="10" allowOverlap="true">
                    <wp:positionH relativeFrom="margin">
                        <wp:align>center</wp:align>
                    </wp:positionH>
                    <wp:positionV relativeFrom="margin">
                        <wp:align>center</wp:align>
                    </wp:positionV>
                    <wp:extent cx="2441542" cy="1828800"/>
                    <wp:wrapSquare wrapText="bothSides"/>
                    <a:graphic>
                    …
                    </a:graphic>
                </wp:anchor>
            </w:drawing>
        </w:r>
        ```
    
        锚元素 ([§20.4.2.3]) 指定该对象不与文本对齐，其子元素指定该对象在页面上水平和垂直居中 ([§20.4.2.10]; [§20.4 .2.11]），并且该文本可以围绕它形成一个正方形（[§20.4.2.17]）。

=== "英文"

    **DrawingML - WordprocessingML Drawing**

    Within a WordprocessingML document, it is possible to include graphical DrawingML objects:

    - Pictures ([§20.2])
    - Locked Canvases ([§20.3])
    - Diagrams ([§21.4])
    - Charts ([§21.2])
    
    When these objects are present in a word processing document, it is necessary to include information which specifies how the objects shall be positioned relative to the paginated document. [Example: Whether the object is displayed in line with text. end example]

    The WordprocessingML Drawing namespace acts in this capacity, specifying all information necessary to anchor and display DrawingML objects within a word processing document

    [Example: Consider a DrawingML picture which must be displayed in the center of the printed page on which it appears, modifying the flow of text as necessary. This object would be specified as follows:
    
    ```xml
    <w:r>
        <w:drawing>
            <wp:anchor relativeHeight="10" allowOverlap="true">
                <wp:positionH relativeFrom="margin">
                    <wp:align>center</wp:align>
                </wp:positionH>
                <wp:positionV relativeFrom="margin">
                    <wp:align>center</wp:align>
                </wp:positionV>
                <wp:extent cx="2441542" cy="1828800"/>
                <wp:wrapSquare wrapText="bothSides"/>
                <a:graphic>
                …
                </a:graphic>
            </wp:anchor>
        </w:drawing>
    </w:r>
    ```
    
    The anchor element ([§20.4.2.3]) specifies that this object is not positioned in line with text, and its child elements specify that the object is centered on the page horizontally and vertically ([§20.4.2.10]; [§20.4.2.11]), and that text can wrap around it in a square ([§20.4.2.17]). end example]

## 20.4.1 目录

=== "中文"

    - 20.4.2 Elements
        - 20.4.2.1 align (Relative Horizontal Alignment)
        - 20.4.2.2 align (Relative Vertical Alignment)
        - 20.4.2.3 anchor (Anchor for Floating DrawingML Object)  
        - 20.4.2.4 cNvGraphicFramePr (Common DrawingML Non-Visual Properties)
        - 20.4.2.5 docPr (Drawing Object Non-Visual Properties)
        - 20.4.2.6 effectExtent (Object Extents Including Effects)
        - 20.4.2.7 extent (Drawing Object Size)
        - 20.4.2.8 inline (Inline DrawingML Object)
        - 20.4.2.9 lineTo (Wrapping Polygon Line End Position)
        - 20.4.2.10 positionH (Horizontal Positioning)  
        - 20.4.2.11 positionV (Vertical Positioning)
        - 20.4.2.12 posOffset (Absolute Position Offset)
        - 20.4.2.13 simplePos (Simple Positioning Coordinates)
        - 20.4.2.14 start (Wrapping Polygon Start)
        - 20.4.2.15 wrapNone (No Text Wrapping)
        - 20.4.2.16 wrapPolygon (Wrapping Polygon)
        - 20.4.2.17 wrapSquare (Square Wrapping)
        - 20.4.2.18 wrapThrough (Through Wrapping)
        - 20.4.2.19 wrapTight (Tight Wrapping)  
        - 20.4.2.20 wrapTopAndBottom (Top and Bottom Wrapping)
        - 20.4.2.21 bg (Background Formatting)
        - 20.4.2.22 bodyPr (Body Properties)  
        - 20.4.2.23 cNvCnPr (Non-Visual Connector Shape Drawing Properties)
        - 20.4.2.24 cNvContentPartPr (Non-Visual Content Part Drawing Properties)
        - 20.4.2.25 cNvFrPr (Non-Visual Graphic Frame Drawing Properties)
        - 20.4.2.26 cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)
        - 20.4.2.27 cNvPr (Non-Visual Drawing Properties)  
        - 20.4.2.28 cNvSpPr (Non-Visual Drawing Properties for a Shape)
        - 20.4.2.29 contentPart (Content Part)
        - 20.4.2.30 extLst (Extension List)
        - 20.4.2.31 graphicFrame (Graphical object container)
        - 20.4.2.32 grpSp (Group Shape)
        - 20.4.2.33 grpSpPr (Group Shape Properties)  
        - 20.4.2.34 linkedTxbx (Textual contents of shape)
        - 20.4.2.35 spPr (Shape Properties)
        - 20.4.2.36 style (Shape Style)
        - 20.4.2.37 txbx (Textual contents of shape)
        - 20.4.2.38 txbxContent (Rich Text Box Content Container)
        - 20.4.2.39 wgp (WordprocessingML Shape Group)
        - 20.4.2.40 whole (Whole E2O Formatting)
        - 20.4.2.41 wpc (WordprocessingML Drawing Canvas)
        - 20.4.2.42 wsp (WordprocessingML Shape)
        - 20.4.2.43 xfrm (2D Transform for Graphic Frames)  
    - 20.4.3 Simple Types
        - 20.4.3.1 ST_AlignH (Relative Horizontal Alignment Positions)
        - 20.4.3.2 ST_AlignV (Vertical Alignment Definition)
        - 20.4.3.3 ST_PositionOffset (Absolute Position Offset Value)
        - 20.4.3.4 ST_RelFromH (Horizontal Relative Positioning)  
        - 20.4.3.5 ST_RelFromV (Vertical Relative Positioning)
        - 20.4.3.6 ST_WrapDistance (Distance from Text)  
        - 20.4.3.7 ST_WrapText (Text Wrapping Location)

=== "英文"

    **Table of Contents**

    This subclause is informative

    - 20.4.2 Elements
        - 20.4.2.1 align (Relative Horizontal Alignment)
        - 20.4.2.2 align (Relative Vertical Alignment)
        - 20.4.2.3 anchor (Anchor for Floating DrawingML Object)  
        - 20.4.2.4 cNvGraphicFramePr (Common DrawingML Non-Visual Properties)
        - 20.4.2.5 docPr (Drawing Object Non-Visual Properties)
        - 20.4.2.6 effectExtent (Object Extents Including Effects)
        - 20.4.2.7 extent (Drawing Object Size)
        - 20.4.2.8 inline (Inline DrawingML Object)
        - 20.4.2.9 lineTo (Wrapping Polygon Line End Position)
        - 20.4.2.10 positionH (Horizontal Positioning)  
        - 20.4.2.11 positionV (Vertical Positioning)
        - 20.4.2.12 posOffset (Absolute Position Offset)
        - 20.4.2.13 simplePos (Simple Positioning Coordinates)
        - 20.4.2.14 start (Wrapping Polygon Start)
        - 20.4.2.15 wrapNone (No Text Wrapping)
        - 20.4.2.16 wrapPolygon (Wrapping Polygon)
        - 20.4.2.17 wrapSquare (Square Wrapping)
        - 20.4.2.18 wrapThrough (Through Wrapping)
        - 20.4.2.19 wrapTight (Tight Wrapping)  
        - 20.4.2.20 wrapTopAndBottom (Top and Bottom Wrapping)
        - 20.4.2.21 bg (Background Formatting)
        - 20.4.2.22 bodyPr (Body Properties)  
        - 20.4.2.23 cNvCnPr (Non-Visual Connector Shape Drawing Properties)
        - 20.4.2.24 cNvContentPartPr (Non-Visual Content Part Drawing Properties)
        - 20.4.2.25 cNvFrPr (Non-Visual Graphic Frame Drawing Properties)
        - 20.4.2.26 cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)
        - 20.4.2.27 cNvPr (Non-Visual Drawing Properties)  
        - 20.4.2.28 cNvSpPr (Non-Visual Drawing Properties for a Shape)
        - 20.4.2.29 contentPart (Content Part)
        - 20.4.2.30 extLst (Extension List)
        - 20.4.2.31 graphicFrame (Graphical object container)
        - 20.4.2.32 grpSp (Group Shape)
        - 20.4.2.33 grpSpPr (Group Shape Properties)  
        - 20.4.2.34 linkedTxbx (Textual contents of shape)
        - 20.4.2.35 spPr (Shape Properties)
        - 20.4.2.36 style (Shape Style)
        - 20.4.2.37 txbx (Textual contents of shape)
        - 20.4.2.38 txbxContent (Rich Text Box Content Container)
        - 20.4.2.39 wgp (WordprocessingML Shape Group)
        - 20.4.2.40 whole (Whole E2O Formatting)
        - 20.4.2.41 wpc (WordprocessingML Drawing Canvas)
        - 20.4.2.42 wsp (WordprocessingML Shape)
        - 20.4.2.43 xfrm (2D Transform for Graphic Frames)  
    - 20.4.3 Simple Types
        - 20.4.3.1 ST_AlignH (Relative Horizontal Alignment Positions)
        - 20.4.3.2 ST_AlignV (Vertical Alignment Definition)
        - 20.4.3.3 ST_PositionOffset (Absolute Position Offset Value)
        - 20.4.3.4 ST_RelFromH (Horizontal Relative Positioning)  
        - 20.4.3.5 ST_RelFromV (Vertical Relative Positioning)
        - 20.4.3.6 ST_WrapDistance (Distance from Text)  
        - 20.4.3.7 ST_WrapText (Text Wrapping Location)

## 20.4.2 元素

=== "中文"

=== "英文"

    **Elements**

### 20.4.2.1 align (相对水平对齐)

=== "中文"

=== "英文"

    **align (Relative Horizontal Alignment)**

### 20.4.2.2 align (相对垂直对齐)

=== "中文"

=== "英文"

    **align (Relative Vertical Alignment)**

### 20.4.2.3 anchor (浮动 DrawingML 对象的锚点)

=== "中文"

=== "英文"

    **anchor (Anchor for Floating DrawingML Object)  **

### 20.4.2.4 cNvGraphicFramePr (常见 DrawingML 非可视属性)

=== "中文"

=== "英文"

    **cNvGraphicFramePr (Common DrawingML Non-Visual Properties)**

### 20.4.2.5 docPr (绘图对象非可视属性)

=== "中文"

=== "英文"

    **docPr (Drawing Object Non-Visual Properties)**

### 20.4.2.6 effectExtent (对象范围（包括效果）)

=== "中文"

=== "英文"

    **effectExtent (Object Extents Including Effects)**

### 20.4.2.7 extent (绘图对象尺寸)

=== "中文"

=== "英文"

    **extent (Drawing Object Size)**

### 20.4.2.8 inline (内联DrawingML对象)

=== "中文"

=== "英文"

    **inline (Inline DrawingML Object)**

### 20.4.2.9 lineTo (包裹多边形线结束位置)

=== "中文"

=== "英文"

    **lineTo (Wrapping Polygon Line End Position)**

### 20.4.2.10 positionH (水平定位)

=== "中文"

=== "英文"

    **positionH (Horizontal Positioning)  **

### 20.4.2.11 positionV (垂直定位)

=== "中文"

=== "英文"

    **positionV (Vertical Positioning)**

### 20.4.2.12 posOffset (绝对位置偏移)

=== "中文"

=== "英文"

    **posOffset (Absolute Position Offset)**

### 20.4.2.13 simplePos (简单定位坐标)

=== "中文"

=== "英文"

    **simplePos (Simple Positioning Coordinates)**

### 20.4.2.14 start (包裹多边形起点)

=== "中文"

=== "英文"

    **start (Wrapping Polygon Start)**

### 20.4.2.15 wrapNone (无文字环绕)

=== "中文"

=== "英文"

    **wrapNone (No Text Wrapping)**

### 20.4.2.16 wrapPolygon (包裹多边形)

=== "中文"

=== "英文"

    **wrapPolygon (Wrapping Polygon)**

### 20.4.2.17 wrapSquare (方形包装)

=== "中文"

=== "英文"

    **wrapSquare (Square Wrapping)**

### 20.4.2.18 wrapThrough (Through 包装)

=== "中文"

=== "英文"

    **wrapThrough (Through Wrapping)**

### 20.4.2.19 wrapTight (Tight 包装)

=== "中文"

=== "英文"

    **wrapTight (Tight Wrapping)**

### 20.4.2.20 wrapTopAndBottom (顶部和底部包装)

=== "中文"

=== "英文"

    **wrapTopAndBottom (Top and Bottom Wrapping)**

### 20.4.2.21 bg (背景格式)

=== "中文"

=== "英文"

    **bg (Background Formatting)**

### 20.4.2.22 bodyPr (正文格式)

=== "中文"

=== "英文"

    **bodyPr (Body Properties)**

### 20.4.2.23 cNvCnPr (非可视连接器形状绘图属性)

=== "中文"

=== "英文"

    **cNvCnPr (Non-Visual Connector Shape Drawing Properties)**

### 20.4.2.24 cNvContentPartPr (非视觉内容零件绘图属性)

=== "中文"

=== "英文"

    **cNvContentPartPr (Non-Visual Content Part Drawing Properties)**

### 20.4.2.25 cNvFrPr (非可视图形框架绘图属性)

=== "中文"

=== "英文"

    **cNvFrPr (Non-Visual Graphic Frame Drawing Properties)**

### 20.4.2.26 cNvGrpSpPr (非可视组形状绘图属性)

=== "中文"

=== "英文"

    **cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)**

### 20.4.2.27 cNvPr (非可视绘图属性)

=== "中文"

=== "英文"

    **cNvPr (Non-Visual Drawing Properties)**

### 20.4.2.28 cNvSpPr (形状的非可视绘图属性)

=== "中文"

=== "英文"

    **cNvSpPr (Non-Visual Drawing Properties for a Shape)**

### 20.4.2.29 contentPart (内容部分)

=== "中文"

=== "英文"

    **contentPart (Content Part)**

### 20.4.2.30 extLst (扩展列表)

=== "中文"

=== "英文"

    **extLst (Extension List)**

### 20.4.2.31 graphicFrame (图形对象容器)

=== "中文"

=== "英文"

    **graphicFrame (Graphical object container)**

### 20.4.2.32 grpSp (团体形态)

=== "中文"

=== "英文"

    **grpSp (Group Shape)**

### 20.4.2.33 grpSpPr (组合形状属性)

=== "中文"

=== "英文"

    **grpSpPr (Group Shape Properties)**

### 20.4.2.34 linkedTxbx (形状的文字内容)

=== "中文"

=== "英文"

    **linkedTxbx (Textual contents of shape)**

### 20.4.2.35 spPr (形状属性)

=== "中文"

=== "英文"

    **spPr (Shape Properties)**

### 20.4.2.36 style (形状样式)

=== "中文"

=== "英文"

    **style (Shape Style)**

### 20.4.2.37 txbx (形状的文字内容)

=== "中文"

=== "英文"

    **txbx (Textual contents of shape)**

### 20.4.2.38 txbxContent (富文本框内容容器)

=== "中文"

=== "英文"

    **txbxContent (Rich Text Box Content Container)**

### 20.4.2.39 wgp (WordprocessingML 形状组合)

=== "中文"

=== "英文"

    **wgp (WordprocessingML Shape Group)**

### 20.4.2.40 whole (整个E2O格式)

=== "中文"

=== "英文"

    **whole (Whole E2O Formatting)**

### 20.4.2.41 wpc (WordprocessingML Drawing Canvas)

=== "中文"

=== "英文"

    **wpc (WordprocessingML Drawing Canvas)**

### 20.4.2.42 wsp (WordprocessingML 形状)

=== "中文"

=== "英文"

    **wsp (WordprocessingML Shape)**

### 20.4.2.43 xfrm (图形框架的2D变换)

=== "中文"

=== "英文"

    **xfrm (2D Transform for Graphic Frames)**

## 20.4.3 简单类型

=== "中文"

=== "英文"

    **Simple Types**

### 20.4.3.1 ST_AlignH (相对水平对齐位置)

=== "中文"

=== "英文"

    **ST_AlignH (Relative Horizontal Alignment Positions)**

### 20.4.3.2 ST_AlignV (垂直对齐定义)

=== "中文"

=== "英文"

    **ST_AlignV (Vertical Alignment Definition)**

### 20.4.3.3 ST_PositionOffset (绝对位置偏置值)

=== "中文"

=== "英文"

    **ST_PositionOffset (Absolute Position Offset Value)**

### 20.4.3.4 ST_RelFromH (水平相对定位)

=== "中文"

=== "英文"

    **ST_RelFromH (Horizontal Relative Positioning)**

### 20.4.3.5 ST_RelFromV (垂直相对定位)

=== "中文"

=== "英文"

    **ST_RelFromV (Vertical Relative Positioning)**

### 20.4.3.6 ST_WrapDistance (与文本的距离)

=== "中文"

=== "英文"

    **ST_WrapDistance (Distance from Text)**

### 20.4.3.7 ST_WrapText (文本换行位置)

=== "中文"

=== "英文"

    **ST_WrapText (Text Wrapping Location)**
