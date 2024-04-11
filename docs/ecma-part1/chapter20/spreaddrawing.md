# 20.5 DrawingML - SpreadsheetML Drawing

=== "中文"

    在 SpreadsheetML 文档中，可以包含图形 DrawingML 对象：

    - Pictures ([§20.2])
    - Locked Canvases ([§20.3])
    - Diagrams ([§21.4])
    - Charts ([§21.2])

    当这些对象出现在电子表格文档中时，有必要包括指定这些对象相对于父工作表如何定位的信息。 [例如: 对象是否锚定到特定行、是否随单元格调整大小等等。 ]
    
    SpreadsheetML Drawing 命名空间发挥此功能，指定在电子表格文档中锚定和显示 DrawingML 对象所需的所有信息。
    
    !!! info "例子"
    
        考虑一张 DrawingML 图片，其左上角和右下角必须锚定到特定单元格，并随着这些单元格的重新定位而调整大小。 该对象将指定如下：

        ```xml
        <xdr:twoCellAnchor>
            <xdr:from>
            …
            </xdr:from>
            <xdr:to>
                …
            </xdr:to>
            <xdr:graphicFrame>
                …
                <a:graphic>
                    <a:graphicData
                        uri="http://purl.oclc.org/ooxml/drawingml/diagram">
                        <dgm:relIds xmlns:dgm="…" xmlns:r="…" r:dm="rId1" r:lo="rId2"
                            r:qs="rId3" r:cs="rId4" />
                    </a:graphicData>
                </a:graphic>
            </xdr:graphicFrame>
        </xdr:twoCellAnchor>
        ```

    `TwoCellAnchor` 元素 ([§20.5.2.33]) 指定该对象锚定到由 `to` ([§20.5.2.32]) 和 `from` ([§20.5.2.15]) 元素指定的单元格。

=== "英文"

    **DrawingML - SpreadsheetML Drawing**

    Within a SpreadsheetML document, it is possible to include graphical DrawingML objects:

    - Pictures ([§20.2])
    - Locked Canvases ([§20.3])
    - Diagrams ([§21.4])
    - Charts ([§21.2])

    When these objects are present in a spreadsheet document, it is necessary to include information which specifies how the objects shall be positioned relative to the parent worksheet. [Example: Whether the object is anchored to a specific row, whether it resizes with cells, and so on. end example]
    
    The SpreadsheetML Drawing namespace acts in this capacity, specifying all information necessary to anchor and display DrawingML objects within a spreadsheet document.
    
    [Example: Consider a DrawingML picture which must be anchored to a specific cell for its top left and bottom right corners, resizing as those cells are relocated. This object would be specified as follows:

    ```xml
    <xdr:twoCellAnchor>
     <xdr:from>
     …
     </xdr:from>
    <xdr:to>
     …
    </xdr:to>
     <xdr:graphicFrame>
     …
     <a:graphic>
     <a:graphicData
     uri="http://purl.oclc.org/ooxml/drawingml/diagram">
     <dgm:relIds xmlns:dgm="…" xmlns:r="…" r:dm="rId1" r:lo="rId2"
     r:qs="rId3" r:cs="rId4" />
     </a:graphicData>
     </a:graphic>
     </xdr:graphicFrame>
    </xdr:twoCellAnchor>
    ```

    The twoCellAnchor element ([§20.5.2.33]) specifies that this object anchored to the cells specified by the to ([§20.5.2.32]) and from ([§20.5.2.15]) elements. end example]

## 20.5.1 目录

=== "中文"

    - 20.5.2 Elements
        - 20.5.2.1 absoluteAnchor (Absolute Anchor Shape Size)
        - 20.5.2.2 blipFill (Picture Fill)  
        - 20.5.2.3 clientData (Client Data)
        - 20.5.2.4 cNvCxnSpPr (Non-Visual Connector Shape Drawing Properties)
        - 20.5.2.5 cNvGraphicFramePr (Non-Visual Graphic Frame Drawing Properties)
        - 20.5.2.6 cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)
        - 20.5.2.7 cNvPicPr (Non-Visual Picture Drawing Properties)
        - 20.5.2.8 cNvPr (Non-Visual Drawing Properties)  
        - 20.5.2.9 cNvSpPr (Connection Non-Visual Shape Properties)
        - 20.5.2.10 col (Column)
        - 20.5.2.11 colOff (Column Offset)
        - 20.5.2.12 contentPart (Content Part)
        - 20.5.2.13 cxnSp (Connection Shape)
        - 20.5.2.14 ext (Shape Extent)
        - 20.5.2.15 from (Starting Anchor Point)
        - 20.5.2.16 graphicFrame (Graphic Frame)
        - 20.5.2.17 grpSp (Group Shape)
        - 20.5.2.18 grpSpPr (Group Shape Properties)  
        - 20.5.2.19 nvCxnSpPr (Non-Visual Properties for a Connection Shape)  
        - 20.5.2.20 nvGraphicFramePr (Non-Visual Properties for a Graphic Frame)
        - 20.5.2.21 nvGrpSpPr (Non-Visual Properties for a Group Shape)
        - 20.5.2.22 nvPicPr (Non-Visual Properties for a Picture)
        - 20.5.2.23 nvSpPr (Non-Visual Properties for a Shape)
        - 20.5.2.24 oneCellAnchor (One Cell Anchor Shape Size)
        - 20.5.2.25 pic (Picture)
        - 20.5.2.26 pos (Position)
        - 20.5.2.27 row (Row)  
        - 20.5.2.28 rowOff (Row Offset)  
        - 20.5.2.29 sp (Shape)  
        - 20.5.2.30 spPr (Shape Properties)
        - 20.5.2.31 style (Shape Style)
        - 20.5.2.32 to (Ending Anchor Point)
        - 20.5.2.33 twoCellAnchor (Two Cell Anchor Shape Size)
        - 20.5.2.34 txBody (Shape Text Body)
        - 20.5.2.35 wsDr (Worksheet Drawing)
        - 20.5.2.36 xfrm (2D Transform for Graphic Frames)  
    - 20.5.3 Simple Types
        - 20.5.3.1 ST_ColID (Column ID)  
        - 20.5.3.2 ST_EditAs (Resizing Behaviors)
        - 20.5.3.3 ST_RowID (Row ID)

=== "英文"

    **Table of Contents**

    This subclause is informative.

    - 20.5.2 Elements
        - 20.5.2.1 absoluteAnchor (Absolute Anchor Shape Size)
        - 20.5.2.2 blipFill (Picture Fill)  
        - 20.5.2.3 clientData (Client Data)
        - 20.5.2.4 cNvCxnSpPr (Non-Visual Connector Shape Drawing Properties)
        - 20.5.2.5 cNvGraphicFramePr (Non-Visual Graphic Frame Drawing Properties)
        - 20.5.2.6 cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)
        - 20.5.2.7 cNvPicPr (Non-Visual Picture Drawing Properties)
        - 20.5.2.8 cNvPr (Non-Visual Drawing Properties)  
        - 20.5.2.9 cNvSpPr (Connection Non-Visual Shape Properties)
        - 20.5.2.10 col (Column)
        - 20.5.2.11 colOff (Column Offset)
        - 20.5.2.12 contentPart (Content Part)
        - 20.5.2.13 cxnSp (Connection Shape)
        - 20.5.2.14 ext (Shape Extent)
        - 20.5.2.15 from (Starting Anchor Point)
        - 20.5.2.16 graphicFrame (Graphic Frame)
        - 20.5.2.17 grpSp (Group Shape)
        - 20.5.2.18 grpSpPr (Group Shape Properties)  
        - 20.5.2.19 nvCxnSpPr (Non-Visual Properties for a Connection Shape)  
        - 20.5.2.20 nvGraphicFramePr (Non-Visual Properties for a Graphic Frame)
        - 20.5.2.21 nvGrpSpPr (Non-Visual Properties for a Group Shape)
        - 20.5.2.22 nvPicPr (Non-Visual Properties for a Picture)
        - 20.5.2.23 nvSpPr (Non-Visual Properties for a Shape)
        - 20.5.2.24 oneCellAnchor (One Cell Anchor Shape Size)
        - 20.5.2.25 pic (Picture)
        - 20.5.2.26 pos (Position)
        - 20.5.2.27 row (Row)  
        - 20.5.2.28 rowOff (Row Offset)  
        - 20.5.2.29 sp (Shape)  
        - 20.5.2.30 spPr (Shape Properties)
        - 20.5.2.31 style (Shape Style)
        - 20.5.2.32 to (Ending Anchor Point)
        - 20.5.2.33 twoCellAnchor (Two Cell Anchor Shape Size)
        - 20.5.2.34 txBody (Shape Text Body)
        - 20.5.2.35 wsDr (Worksheet Drawing)
        - 20.5.2.36 xfrm (2D Transform for Graphic Frames)  
    - 20.5.3 Simple Types
        - 20.5.3.1 ST_ColID (Column ID)  
        - 20.5.3.2 ST_EditAs (Resizing Behaviors)
        - 20.5.3.3 ST_RowID (Row ID)

## 20.5.2 元素

=== "中文"

=== "英文"

    **Elements**

### 20.5.2.1 absoluteAnchor (绝对锚形状尺寸)

=== "中文"

=== "英文"

    **absoluteAnchor (Absolute Anchor Shape Size)**

### 20.5.2.2 blipFill (图片填充)

=== "中文"

=== "英文"

    **blipFill (Picture Fill)**

### 20.5.2.3 clientData (客户端数据)

=== "中文"

=== "英文"

    **clientData (Client Data)**

### 20.5.2.4 cNvCxnSpPr (非可视连接器形状绘图属性)

=== "中文"

=== "英文"

    **cNvCxnSpPr (Non-Visual Connector Shape Drawing Properties)**

### 20.5.2.5 cNvGraphicFramePr (非可视图形框架绘图属性)

=== "中文"

=== "英文"

    **cNvGraphicFramePr (Non-Visual Graphic Frame Drawing Properties)**

### 20.5.2.6 cNvGrpSpPr (非可视组形状绘图属性)

=== "中文"

=== "英文"

    **cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)**

### 20.5.2.7 cNvPicPr (非视觉绘图属性)

=== "中文"

=== "英文"

    **cNvPicPr (Non-Visual Picture Drawing Properties)**

### 20.5.2.8 cNvPr (非可视绘图属性)

=== "中文"

=== "英文"

    **cNvPr (Non-Visual Drawing Properties)**

### 20.5.2.9 cNvSpPr (连接非视觉形状属性)

=== "中文"

=== "英文"

    **cNvSpPr (Connection Non-Visual Shape Properties)**

### 20.5.2.10 col (列)

=== "中文"

=== "英文"

    **col (Column)**

### 20.5.2.11 colOff (列偏移)

=== "中文"

=== "英文"

    **colOff (Column Offset)**

### 20.5.2.12 contentPart (内容部分)

=== "中文"

=== "英文"

    **contentPart (Content Part)**

### 20.5.2.13 cxnSp (连接相撞)

=== "中文"

=== "英文"

    **cxnSp (Connection Shape)**

### 20.5.2.14 ext (形状范围)

=== "中文"

=== "英文"

    **ext (Shape Extent)**

### 20.5.2.15 from (起始锚点)

=== "中文"

=== "英文"

    **from (Starting Anchor Point)**

### 20.5.2.16 graphicFrame (图框)

=== "中文"

=== "英文"

    **graphicFrame (Graphic Frame)**

### 20.5.2.17 grpSp (组合形状)

=== "中文"

=== "英文"

    **grpSp (Group Shape)**

### 20.5.2.18 grpSpPr (组合形状属性)

=== "中文"

=== "英文"

    **grpSpPr (Group Shape Properties)**

### 20.5.2.19 nvCxnSpPr (连接形状的非视觉属性)

=== "中文"

=== "英文"

    **nvCxnSpPr (Non-Visual Properties for a Connection Shape)**

### 20.5.2.20 nvGraphicFramePr (图形框架的非视觉属性)

=== "中文"

=== "英文"

    **nvGraphicFramePr (Non-Visual Properties for a Graphic Frame)**

### 20.5.2.21 nvGrpSpPr (组形状的非视觉属性)

=== "中文"

=== "英文"

    **nvGrpSpPr (Non-Visual Properties for a Group Shape)**

### 20.5.2.22 nvPicPr (图片的非视觉属性)

=== "中文"

=== "英文"

    **nvPicPr (Non-Visual Properties for a Picture)**

### 20.5.2.23 nvSpPr (形状的非视觉属性)

=== "中文"

=== "英文"

    **nvSpPr (Non-Visual Properties for a Shape)**

### 20.5.2.24 oneCellAnchor (一单元格锚定形状尺寸)

=== "中文"

=== "英文"

    **oneCellAnchor (One Cell Anchor Shape Size)**

### 20.5.2.25 pic (图片)

=== "中文"

=== "英文"

    **pic (Picture)**

### 20.5.2.26 pos (位置)

=== "中文"

=== "英文"

    **pos (Position)**

### 20.5.2.27 row (行)

=== "中文"

=== "英文"

    **row (Row)**

### 20.5.2.28 rowOff (行偏移)

=== "中文"

=== "英文"

    **rowOff (Row Offset)**

### 20.5.2.29 sp (形状)

=== "中文"

=== "英文"

    **sp (Shape)**

### 20.5.2.30 spPr (形状属性)

=== "中文"

=== "英文"

    **spPr (Shape Properties)**

### 20.5.2.31 style (形状样式)

=== "中文"

=== "英文"

    **style (Shape Style)**

### 20.5.2.32 to (结束锚点)

=== "中文"

=== "英文"

    **to (Ending Anchor Point)**

### 20.5.2.33 twoCellAnchor (两单元锚定形状尺寸)

=== "中文"

=== "英文"

    **twoCellAnchor (Two Cell Anchor Shape Size)**

### 20.5.2.34 txBody (形状文本正文)

=== "中文"

=== "英文"

    **EltxBody (Shape Text Body)ements**

### 20.5.2.35 wsDr (工作表绘图)

=== "中文"

=== "英文"

    **wsDr (Worksheet Drawing)**

### 20.5.2.36 xfrm (图形框架的 2D 变换)

=== "中文"

=== "英文"

    **xfrm (2D Transform for Graphic Frames)**

## 20.5.3 简单类型

=== "中文"

=== "英文"

    **Simple Types**

### 20.5.3.1 ST_ColID (列ID)

=== "中文"

=== "英文"

    **ST_ColID (Column ID)**

### 20.5.3.2 ST_EditAs (调整行为大小)

=== "中文"

=== "英文"

    **ST_EditAs (Resizing Behaviors)**

### 20.5.3.3 ST_RowID (行ID)

=== "中文"

=== "英文"

    **ST_RowID (Row ID)**
