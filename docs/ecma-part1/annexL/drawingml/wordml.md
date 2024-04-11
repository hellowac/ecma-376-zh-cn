
# L.4.11 WordprocessingML Drawing

=== "中文"

    在 WordprocessingML 文档中，可以包含图形 DrawingML 对象：

    - 图表 - Charts
    - 示意图 - Diagrams
    - 锁定的Canvases - Locked Canvases
    - 图片 - Pictures
  
    当这些对象出现在文字处理文档中时，有必要包括指定这些对象相对于分页文档如何定位的信息。

    WordprocessingML Drawing 命名空间发挥此功能，指定在字处理文档中锚定和显示 DrawingML 对象所需的所有信息。

    考虑一张 DrawingML 图片，该图片将显示在其出现的打印页面的中心，并根据需要修改文本流。 该对象将指定如下：

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

    锚元素指定该对象不与文本对齐，其子元素指定该对象在页面上水平和垂直居中，并且文本可以在其周围环绕成正方形。

=== "英文"

    **WordprocessingML Drawing**

    Within a WordprocessingML document, it is possible to include graphical DrawingML objects:

    - Charts
    - Diagrams
    - Locked Canvases
    - Pictures
  
    When these objects are present in a word processing document, it is necessary to include information that specifies how the objects are to be positioned relative to the paginated document.

    The WordprocessingML Drawing namespace acts in this capacity, specifying all information necessary to     anchor and display DrawingML objects within a word processing document.

    Consider a DrawingML picture that is to displayed in the center of the printed page on which it appears, modifying the flow of text as necessary. This object would be specified as follows:

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

    The anchor element specifies that this object is not positioned in-line with text, and its child elements specify that the object is centered on the page horizontally and vertically, and that text can wrap around it in a square.

## L.4.11.1 Object Anchoring

=== "中文"

=== "英文"

    **aaaa**

## L.4.11.2 Text Wrapping

=== "中文"

=== "英文"

    **aaaa**
