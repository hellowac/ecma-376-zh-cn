# 19.7 简单类型

=== "中文"

    这是专用于PresentationML 的简单类型的完整列表。

=== "英文"

    **Simple Types**

    This is the complete list of simple types dedicated to PresentationML.

## 19.7.1 ST_BookmarkIdSeed (书签 ID 种子)

=== "中文"

    此简单类型指定书签 ID 种子值的约束。

    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 此简单类型的最小值大于或等于 1。
    - 此简单类型的最大值小于 2147483648。
    
    [Note: 此简单类型的内容模型 (ST_BookmarkIdSeed) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_BookmarkIdSeed (Bookmark ID Seed)**

    This simple type specifies constraints for value of the Bookmark ID seed.

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 1.
    - This simple type has a maximum value of less than 2147483648.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_BookmarkIdSeed) is located in §A.3. end note]

## 19.7.2 ST_Direction (方向)

=== "中文"

    这种简单类型定义水平或垂直方向。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    horz (水平的)
                </td>
                <td>
                    定义水平方向。
                </td>
            </tr>
            <tr>
                <td>
                    vert (垂直的)
                </td>
                <td>
                    定义垂直方向。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_Direction) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_Direction (Direction)**

    This simple type defines a direction of either horizontal or vertical.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    horz (Horizontal)
                </td>
                <td>
                    Defines a horizontal direction.
                </td>
            </tr>
            <tr>
                <td>
                    vert (Vertical)
                </td>
                <td>
                    Defines a vertical direction.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Direction) is located in §A.3. end note]

## 19.7.3 ST_Index (索引)

=== "中文"

    这个简单的类型定义了对象在有序列表中的位置。

    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。
    
    [Note: 此简单类型的内容模型 (ST_Index) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_Index (Index)**

    This simple type defines the position of an object in an ordered list.

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Index) is located in §A.3. end note]

## 19.7.4 ST_IterateType (迭代类型)

=== "中文"

    这个简单类型指定如何将动画应用到目标元素的子元素上。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    el (元素)
                </td>
                <td>
                    按元素迭代。
                </td>
            </tr>
            <tr>
                <td>
                    lt (字母)
                </td>
                <td>
                    按字母迭代。
                </td>
            </tr>
            <tr>
                <td>
                    wd (字)
                </td>
                <td>
                    按 字 进行迭代。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_IterateType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_IterateType (Iterate Type)**

    This simple type specifies how the animation is applied over subelements of the target element.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    el (Element)
                </td>
                <td>
                    Iterate by element.
                </td>
            </tr>
            <tr>
                <td>
                    lt (Letter)
                </td>
                <td>
                    Iterate by Letter.
                </td>
            </tr>
            <tr>
                <td>
                    wd (Word)
                </td>
                <td>
                    Iterate by Word.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_IterateType) is located in §A.3. end note]

## 19.7.5 ST_Name (名称字符串)

=== "中文"

    这种简单类型指定一个名称，例如评论作者或自定义节目的名称。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。
    
    [Note: 此简单类型的内容模型 (ST_Name) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_Name (Name string)**

    This simple type specifies a name, such as for a comment author or custom show.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Name) is located in §A.3. end note]

## 19.7.6 ST_OleObjectFollowColorScheme (遵循配色方案的嵌入对象)

=== "中文"

    此简单类型确定嵌入对象是否重新着色以反映配色方案的更改。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    full (全部)
                </td>
                <td>
                    设置此枚举会导致嵌入对象响应演示文稿中颜色方案的所有更改.
                </td>
            </tr>
            <tr>
                <td>
                    none (无) 
                </td>
                <td>
                    设置此枚举会导致嵌入对象不响应演示文稿中颜色方案的更改.
                </td>
            </tr>
            <tr>
                <td>
                    textAndBackground (文字和背景)
                </td>
                <td>
                    设置此枚举会导致嵌入对象仅响应演示文稿中配色方案的文本和背景颜色的更改。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_OleObjectFollowColorScheme) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_OleObjectFollowColorScheme (Embedded object to Follow Color Scheme)**

    This simple type determines if the Embedded object is re-colored to reflect changes to the color schemes.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    full (Full)
                </td>
                <td>
                    Setting this enumeration causes the Embedded object to respond to all changes in the color scheme in the presentation.
                </td>
            </tr>
            <tr>
                <td>
                    none (None) 
                </td>
                <td>
                    Setting this enumeration causes the Embedded object to not respond to changes in the color scheme in the presentation.
                </td>
            </tr>
            <tr>
                <td>
                    textAndBackground (Text and Background)
                </td>
                <td>
                    Setting this enumeration causes the Embedded object to respond only to changes in the text and background colors of the color scheme in the presentation.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_OleObjectFollowColorScheme) is located in §A.3. end note]

## 19.7.7 ST_PhotoAlbumFrameShape (相片遮罩的相册形状)

=== "中文"

    这个简单的类型指定相册演示中相框类型的值。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    frameStyle1 (长方形相框)
                </td>
                <td>
                    ![19pml-7.png](./imgs/19pml-7.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle2 (圆角矩形相框)
                </td>
                <td>
                    ![19pml-8.png](./imgs/19pml-8.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle3 (简单的白色相框)
                </td>
                <td>
                    ![19pml-9.png](./imgs/19pml-9.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle4 (简单的黑色相框)
                </td>
                <td>
                    ![19pml-10.png](./imgs/19pml-10.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle5 (复合黑色相框)
                </td>
                <td>
                    ![19pml-11.png](./imgs/19pml-11.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle6 (中心阴影相框)
                </td>
                <td>
                    ![19pml-12.png](./imgs/19pml-12.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle7 (软边相框)
                </td>
                <td>
                    ![19pml-13.png](./imgs/19pml-13.png)
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PhotoAlbumFrameShape) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PhotoAlbumFrameShape (Photo Album Shape for Photo Mask)**

    This simple type specifies the values for photo frame types within a photo album presentation.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    frameStyle1 (Rectangle Photo Frame)
                </td>
                <td>
                    ![19pml-7.png](./imgs/19pml-7.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle2 (Rounded Rectangle Photo Frame)
                </td>
                <td>
                    ![19pml-8.png](./imgs/19pml-8.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle3 (Simple White Photo Frame)
                </td>
                <td>
                    ![19pml-9.png](./imgs/19pml-9.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle4 (Simple Black Photo Frame)
                </td>
                <td>
                    ![19pml-10.png](./imgs/19pml-10.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle5 (Compound Black Photo Frame)
                </td>
                <td>
                    ![19pml-11.png](./imgs/19pml-11.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle6 (Center Shadow Photo Frame)
                </td>
                <td>
                    ![19pml-12.png](./imgs/19pml-12.png)
                </td>
            </tr>
            <tr>
                <td>
                    frameStyle7 (Soft Edge Photo Frame)
                </td>
                <td>
                    ![19pml-13.png](./imgs/19pml-13.png)
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PhotoAlbumFrameShape) is located in §A.3. end note]

## 19.7.8 ST_PhotoAlbumLayout (相册布局定义)

=== "中文"

    这个简单的类型指定相册演示文稿中照片布局的值。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    1pic (每张幻灯片 1 张照片)
                </td>
                <td>
                    ![19pml-14.png](./imgs/19pml-14.png)</br></br>
                    指定相册幻灯片应有一张图片，在没有标题的幻灯片上水平和垂直居中。
                </td>
            </tr>
            <tr>
                <td>
                    1picTitle (每张幻灯片 1 张照片（带标题）)
                </td>
                <td>
                    ![19pml-15.png](./imgs/19pml-15.png)</br></br>
                    指定相册幻灯片应有一张图片和一个标题文本框，在幻灯片上水平和垂直居中。
                </td>
            </tr>
            <tr>
                <td>
                    2pic (每张幻灯片 2 张照片)
                </td>
                <td>
                    ![19pml-16.png](./imgs/19pml-16.png)</br></br>
                    指定相册幻灯片应包含两张大小相同的图片，并排放置，水平和垂直居中，幻灯片上没有标题。
                </td>
            </tr>
            <tr>
                <td>
                    2picTitle (每张幻灯片 2 张照片（带标题）)
                </td>
                <td>
                    ![19pml-17.png](./imgs/19pml-17.png)</br></br>
                    指定相册幻灯片应包含两张尺寸相同的图片，并排放置，单个标题文本框位于它们上方，在幻灯片上水平和垂直地共同居中。
                </td>
            </tr>
            <tr>
                <td>
                    4pic (每张幻灯片 4 张照片)
                </td>
                <td>
                    ![19pml-18.png](./imgs/19pml-18.png)</br></br>
                    指定相册幻灯片应有四张相同大小的图片，位于二乘二的矩阵中，水平和垂直居中，位于没有标题的幻灯片上。
                </td>
            </tr>
            <tr>
                <td>
                    4picTitle (每张幻灯片 4 张照片（带标题）)
                </td>
                <td>
                    ![19pml-19.png](./imgs/19pml-19.png)</br></br>
                    指定相册幻灯片应包含四张相同大小的图片，放置在二乘二的矩阵中，单个标题文本框位于矩阵上方，在幻灯片上水平和垂直居中。
                </td>
            </tr>
            <tr>
                <td>
                    fitToSlide (适合幻灯片的照片)
                </td>
                <td>
                    ![19pml-20.png](./imgs/19pml-20.png)</br></br>
                    指定相册幻灯片应该有一张图片，拉伸以适合整个幻灯片大小，没有标题.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PhotoAlbumLayout) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PhotoAlbumLayout (Photo Album Layout Definition)**

    This simple type specifies the values for photo layouts within a photo album presentation.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    1pic (1 Photo per Slide)
                </td>
                <td>
                    ![19pml-14.png](./imgs/19pml-14.png)</br></br>
                    Specifies that photo album slides should have a single picture, centered horizontally and vertically, on the slide with no title.
                </td>
            </tr>
            <tr>
                <td>
                    1picTitle (1 Photo per Slide with Titles)
                </td>
                <td>
                    ![19pml-15.png](./imgs/19pml-15.png)</br></br>
                    Specifies that photo album slides should have a single picture and a single title text box, centered horizontally and vertically, on the slide.
                </td>
            </tr>
            <tr>
                <td>
                    2pic (2 Photos per Slide)
                </td>
                <td>
                    ![19pml-16.png](./imgs/19pml-16.png)</br></br>
                    Specifies that photo album slides should have two pictures of the same size, positioned side-by-side, centered horizontally and vertically, on the slide with no title.
                </td>
            </tr>
            <tr>
                <td>
                    2picTitle (2 Photos per Slide with Titles)
                </td>
                <td>
                    ![19pml-17.png](./imgs/19pml-17.png)</br></br>
                    Specifies that photo album slides should have two pictures of the same size, positioned side-by-side, with a single title text box centered over them, collectively centered horizontally and vertically, on the slide.
                </td>
            </tr>
            <tr>
                <td>
                    4pic (4 Photos per Slide)
                </td>
                <td>
                    ![19pml-18.png](./imgs/19pml-18.png)</br></br>
                    Specifies that photo album slides should have four pictures of the same size, positioned in a two-by-two matrix, centered horizontally and vertically, on the slide with no title.
                </td>
            </tr>
            <tr>
                <td>
                    4picTitle (4 Photos per Slide with Titles)
                </td>
                <td>
                    ![19pml-19.png](./imgs/19pml-19.png)</br></br>
                    Specifies that photo album slides should have four pictures of the same size, positioned in a two-by-two matrix, with a single title text box centered over the matrix, centered horizontally and vertically, on the slide.
                </td>
            </tr>
            <tr>
                <td>
                    fitToSlide (Fit Photos to Slide)
                </td>
                <td>
                    ![19pml-20.png](./imgs/19pml-20.png)</br></br>
                    Specifies that photo album slides should have a single picture, stretched to fit the entire slide size, with no title.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PhotoAlbumLayout) is located in §A.3. end note]

## 19.7.9 ST_PlaceholderSize (占位符大小)

=== "中文"

    这种简单的类型有助于存储占位符的大小。 该尺寸是相对于母版上的正文占位符来描述的。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    full (全部)
                </td>
                <td>
                    指定占位符应采用母版上正文占位符的完整大小。
                </td>
            </tr>
            <tr>
                <td>
                    half (一半) 
                </td>
                <td>
                    指定占位符应采用母版上主体占位符大小的一半。 垂直或水平半尺寸？ 需要一张图片。
                </td>
            </tr>
            <tr>
                <td>
                    quarter (四分之一) 
                </td>
                <td>
                    指定占位符应采用母版上正文占位符大小的四分之一。 图片会有帮助
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PlaceholderSize) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PlaceholderSize (Placeholder Size)**

    This simple type facilitates the storing of the size of the placeholder. This size is described relative to the body placeholder on the master.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    full (Full)
                </td>
                <td>
                    Specifies that the placeholder should take the full size of the body placeholder on the master.
                </td>
            </tr>
            <tr>
                <td>
                    half (Half) 
                </td>
                <td>
                    Specifies that the placeholder should take the half size of the body placeholder on the master. Half size vertically or horizontally? Needs a picture.
                </td>
            </tr>
            <tr>
                <td>
                    quarter (Quarter) 
                </td>
                <td>
                    Specifies that the placeholder should take a quarter of the size of the body placeholder on the master. Picture would be helpful
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PlaceholderSize) is located in §A.3. end note]

## 19.7.10 ST_PlaceholderType (占位符 ID)

=== "中文"

    这种简单的类型有助于存储占位符应包含的内容类型。
    
    [Note: 某些占位符类型不适用于所有 SlideBase 类型. end note]

    此简单类型的内容是 W3C XML 架构Token数据类型的限制.

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    body (正文) 
                </td>
                <td>
                    包含正文。 允许幻灯片、幻灯片布局、幻灯片母版、注释、注释母版。 幻灯片和幻灯片布局可以是水平或垂直的。
                </td>
            </tr>
            <tr>
                <td>
                    chart (图表) 
                </td>
                <td>
                    包含图表或图形。 特种。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    clipArt (剪贴画) 
                </td>
                <td>
                    包含单个剪贴画图像。 特种。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    ctrTitle (居中标题)
                </td>
                <td>
                    包含旨在位于幻灯片中央的标题。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    dgm (绘制/diagram) 
                </td>
                <td>
                    包含绘制，特别的类型，允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    dt (日期和时间)
                </td>
                <td>
                    包含日期和时间。 允许幻灯片、幻灯片布局、幻灯片母版、注释、注释母版、讲义母版
                </td>
            </tr>
            <tr>
                <td>
                    ftr (页脚)
                </td>
                <td>
                    包含要在文档中用作页脚的文本。 允许幻灯片、幻灯片布局、幻灯片母版、注释、注释母版、讲义母版
                </td>
            </tr>
            <tr>
                <td>
                    hdr (标头)
                </td>
                <td>
                    包含用作文档标题的文本。 允许用于笔记、笔记大师、讲义大师。
                </td>
            </tr>
            <tr>
                <td>
                    media (多媒体) 
                </td>
                <td>
                    包含多媒体内容，例如音频或影片剪辑。 特种。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    obj (对象)
                </td>
                <td>
                    包含任何内容类型。 特种。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    pic (图片)
                </td>
                <td>
                    包含一张图片。 特种。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    sldImg (幻灯片图像)
                </td>
                <td>
                    包含幻灯片的图像。 允许用于注释和注释大师。
                </td>
            </tr>
            <tr>
                <td>
                    sldNum (幻灯片编号)
                </td>
                <td>
                    包含幻灯片的编号。 允许幻灯片、幻灯片布局、幻灯片母版、注释、注释母版、讲义母版
                </td>
            </tr>
            <tr>
                <td>
                    subTitle (副标题)
                </td>
                <td>
                    包含副标题。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    tbl (表格)
                </td>
                <td>
                    包含一个表。 特别的类型。 允许幻灯片和幻灯片布局。
                </td>
            </tr>
            <tr>
                <td>
                    title (标题)
                </td>
                <td>
                    包含幻灯片标题。 允许用于幻灯片、幻灯片布局和幻灯片母版。 幻灯片和幻灯片布局可以是水平或垂直的。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PlaceholderType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PlaceholderType (Placeholder IDs)**

    This simple type facilitates the storing of the content type a placeholder should contain.
    
    [Note: Some placeholder types are not allowed for all SlideBase types. end note]

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    body (Body) 
                </td>
                <td>
                    Contains body text. Allowed for Slide, Slide Layout, Slide Master, Notes, Notes Master. Can be horizontal or vertical on Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    chart (Chart) 
                </td>
                <td>
                    Contains a chart or graph. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    clipArt (Clip Art) 
                </td>
                <td>
                    Contains a single clip art image. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    ctrTitle (Centered Title)
                </td>
                <td>
                    Contains a title intended to be centered on the slide. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    dgm (Diagram) 
                </td>
                <td>
                    Contains a diagram. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    dt (Date and Time)
                </td>
                <td>
                    Contains the date and time. Allowed for Slide, Slide Layout, Slide Master, Notes, Notes Master, Handout Master
                </td>
            </tr>
            <tr>
                <td>
                    ftr (Footer)
                </td>
                <td>
                    Contains text to be used as a footer in the document. Allowed for Slide, Slide Layout, Slide Master, Notes, Notes Master, Handout Master
                </td>
            </tr>
            <tr>
                <td>
                    hdr (Header)
                </td>
                <td>
                    Contains text to be used as a header for the document. Allowed for Notes, Notes Master, Handout Master .
                </td>
            </tr>
            <tr>
                <td>
                    media (Media) 
                </td>
                <td>
                    Contains multimedia content such as audio or a movie clip. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    obj (Object)
                </td>
                <td>
                    Contains any content type. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    pic (Picture)
                </td>
                <td>
                    Contains a picture. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    sldImg (Slide Image)
                </td>
                <td>
                    Contains an image of the slide. Allowed for Notes and Notes Master.
                </td>
            </tr>
            <tr>
                <td>
                    sldNum (Slide Number)
                </td>
                <td>
                    Contains the number of a slide. Allowed for Slide, Slide Layout, Slide Master, Notes, Notes Master, Handout Master
                </td>
            </tr>
            <tr>
                <td>
                    subTitle (Subtitle)
                </td>
                <td>
                    Contains a subtitle. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    tbl (Table)
                </td>
                <td>
                    Contains a table. Special type. Allowed for Slide and Slide Layout.
                </td>
            </tr>
            <tr>
                <td>
                    title (Title)
                </td>
                <td>
                    Contains a slide title. Allowed for Slide, Slide Layout and Slide Master. Can be horizontal or vertical on Slide and Slide Layout.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PlaceholderType) is located in §A.3. end note]

## 19.7.11 ST_PrintColorMode (打印色彩模式)

=== "中文"

    此简单类型指定打印演示文稿文档时应使用的颜色模式。
    
    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    bw (黑白模式)
                </td>
                <td>
                    打印只能是黑白的
                </td>
            </tr>
            <tr>
                <td>
                    clr (色彩模式) 
                </td>
                <td>
                    打印应为全彩
                </td>
            </tr>
            <tr>
                <td>
                    gray (灰度模式)
                </td>
                <td>
                    打印只能是灰度
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PrintColorMode) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PrintColorMode (Print Color Mode)**

    This simple type specifies the color mode that should be used when printing a presentation document.
    
    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    bw (Black and White Mode)
                </td>
                <td>
                    Print should be in Black and White only
                </td>
            </tr>
            <tr>
                <td>
                    clr (Color Mode) 
                </td>
                <td>
                    Print should be in Full Color
                </td>
            </tr>
            <tr>
                <td>
                    gray (Grayscale Mode)
                </td>
                <td>
                    Print should be in Grayscale only
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PrintColorMode) is located in §A.3. end note]

## 19.7.12 ST_PrintWhat (默认打印输出)

=== "中文"

    这个简单的类型指定打印时应使用的默认打印布局

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    handouts1 (1 张幻灯片/讲义页)
                </td>
                <td>
                    1 幻灯片和讲义 应使用的页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    handouts2 (2 幻灯片/讲义页) 
                </td>
                <td>
                    2 幻灯片和讲义 应使的用页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    handouts3 (3 幻灯片/讲义页)
                </td>
                <td>
                    3 幻灯片和讲义 应使的用页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    handouts4 (4 幻灯片/讲义页)
                </td>
                <td>
                    4 幻灯片和讲义 应使的用页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    handouts6 (6 幻灯片/讲义页) 
                </td>
                <td>
                    6 幻灯片和讲义 应使的用页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    handouts9 (9 幻灯片/讲义页)
                </td>
                <td>
                    9 幻灯片和讲义 应使的用页面布局。
                </td>
            </tr>
            <tr>
                <td>
                    notes (笔记) 
                </td>
                <td>
                    应使用的注释布局。
                </td>
            </tr>
            <tr>
                <td>
                    outline (大纲)
                </td>
                <td>
                    应使用的大纲布局。
                </td>
            </tr>
            <tr>
                <td>
                    slides (幻灯片) 
                </td>
                <td>
                    幻灯片应使用的布局
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_PrintWhat) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_PrintWhat (Default print output)**

    This simple type specifies the default print layout that should be used when printing

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    handouts1 (1 Slide / Handout Page)
                </td>
                <td>
                    1 Slide and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    handouts2 (2 Slide / Handout Page) 
                </td>
                <td>
                    2 Slide and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    handouts3 (3 Slide / Handout Page)
                </td>
                <td>
                    3 Slide and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    handouts4 (4 Slide / Handout Page)
                </td>
                <td>
                    4 Slides and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    handouts6 (6 Slide / Handout Page) 
                </td>
                <td>
                    6 Slides and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    handouts9 (9 Slide / Handout Page)
                </td>
                <td>
                    9 Slides and Handout Page layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    notes (Notes) 
                </td>
                <td>
                    Notes layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    outline (Outline)
                </td>
                <td>
                    Outline layout should be used.
                </td>
            </tr>
            <tr>
                <td>
                    slides (Slides) 
                </td>
                <td>
                    Slides layout should be used.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PrintWhat) is located in §A.3. end note]

## 19.7.13 ST_SlideId (幻灯片标识符)

=== "中文"

    这个简单类型指定幻灯片标识符允许的编号。

    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 此简单类型的最大值小于 2147483648。
    - 此简单类型的最小值大于或等于 256。
  
    [Note: 此简单类型的内容模型 (ST_SlideId) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideId (Slide Identifier)**

    This simple type specifies the allowed numbering for the slide identifier.

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a maximum value of less than 2147483648.
    - This simple type has a minimum value of greater than or equal to 256.
  
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideId) is located in §A.3. end note]

## 19.7.14 ST_SlideLayoutId (幻灯片布局 ID)

=== "中文"

    这个简单的类型设置幻灯片布局 id 值的范围。 该布局 ID 用于识别不同的幻灯片布局设计.
    
    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 此简单类型的最小值大于或等于 2147483648.

    [Note: 此简单类型的内容模型 (ST_SlideLayoutId) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideLayoutId (Slide Layout ID)**

    This simple type sets the bounds for the slide layout id value. This layout id is used to identify the different slide layout designs.
    
    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 2147483648.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideLayoutId) is located in §A.3. end note]

## 19.7.15 ST_SlideLayoutType (幻灯片布局类型)

=== "中文"

    这种简单的类型定义了幻灯片上内容的排列。 每种布局类型并不与占位符的精确位置相关，而是提供内容类型和占位符位置的高级描述。 应用程序可以使用此信息来帮助在不同布局之间进行映射。 应用程序可以选择通过其用户界面使用这些布局中的哪一个（如果有）。
    
    每个布局包含零个或多个占位符，每个占位符都有特定的内容类型。 “对象”占位符可以包含任何类型的数据。 媒体占位符用于保存视频或音频剪辑。 枚举值描述包括简单类型的每个值的示例布局的图示。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    blank (幻灯片布局类型枚举（空白）)
                </td>
                <td>
                    ![img](./imgs/19pml-21.png)
                    Blank
                </td>
            </tr>
            <tr>
                <td>
                    chart (Chart)
                </td>
                <td>
                    ![img](./imgs/19pml-22.png)
                    标题和图表
                </td>
            </tr>
            <tr>
                <td>
                    chartAndTx (幻灯片布局类型枚举（图表和文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-23.png)
                    标题、图表在左边，文字在右边
                </td>
            </tr>
            <tr>
                <td>
                    clipArtAndTx (剪贴画和文本)
                </td>
                <td>
                    ![img](./imgs/19pml-24.png)
                    标题，左边是剪贴画，右边是文字
                </td>
            </tr>
            <tr>
                <td>
                    clipArtAndVertTx (剪贴画和垂直文本)
                </td>
                <td>
                    ![img](./imgs/19pml-25.png)
                    标题，左侧为剪贴画，右侧为垂直文本
                </td>
            </tr>
            <tr>
                <td>
                    cust (幻灯片布局类型枚举（自定义）)
                </td>
                <td>
                    用户定义的自定义布局
                </td>
            </tr>
            <tr>
                <td>
                    dgm (幻灯片布局类型枚举（图表/diagram）)
                </td>
                <td>
                    ![img](./imgs/19pml-26.png)
                    标题和图表
                </td>
            </tr>
            <tr>
                <td>
                    fourObj (四个对象)
                </td>
                <td>
                    ![img](./imgs/19pml-27.png)
                    标题和四个对象
                </td>
            </tr>
            <tr>
                <td>
                    mediaAndTx (幻灯片布局类型枚举（媒体和文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-28.png)
                    标题和四个对象
                </td>
            </tr>
            <tr>
                <td>
                    obj (标题和对象)
                </td>
                <td>
                    ![img](./imgs/19pml-29.png)
                    标题和对象
                </td>
            </tr>
            <tr>
                <td>
                    objAndTwoObj (对象和两个对象)
                </td>
                <td>
                    ![img](./imgs/19pml-30.png)
                    标题，左侧 1 个对象，右侧 2 个对象
                </td>
            </tr>
            <tr>
                <td>
                    objAndTx (幻灯片布局类型枚举（对象和文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-31.png)
                    标题、对象在左边，文本在右边
                </td>
            </tr>
            <tr>
                <td>
                    objOnly (对象)
                </td>
                <td>
                    ![img](./imgs/19pml-32.png)
                    仅对象
                </td>
            </tr>
            <tr>
                <td>
                    objOverTx (幻灯片布局类型枚举（对象优于文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-33.png)
                    标题、对象在顶部、文本在底部
                </td>
            </tr>
            <tr>
                <td>
                    objTx (标题、对象和说明)
                </td>
                <td>
                    ![img](./imgs/19pml-34.png)
                    标题、对象和说明文本
                </td>
            </tr>
            <tr>
                <td>
                    picTx (图片和说明文字)
                </td>
                <td>
                    ![img](./imgs/19pml-35.png)
                    标题、图片和说明文字
                </td>
            </tr>
            <tr>
                <td>
                    secHead (节标题)
                </td>
                <td>
                    ![img](./imgs/19pml-36.png)
                    节标题和副标题文本
                </td>
            </tr>
            <tr>
                <td>
                    tbl (幻灯片布局类型枚举（表格）)
                </td>
                <td>
                    ![img](./imgs/19pml-37.png)
                    标题和表格
                </td>
            </tr>
            <tr>
                <td>
                    title (幻灯片布局类型枚举（标题）)
                </td>
                <td>
                    ![img](./imgs/19pml-38.png)
                    具有居中标题和副标题占位符的标题布局
                </td>
            </tr>
            <tr>
                <td>
                    titleOnly (幻灯片布局类型枚举（仅限标题）)
                </td>
                <td>
                    ![img](./imgs/19pml-39.png)
                    仅标题
                </td>
            </tr>
            <tr>
                <td>
                    twoColTx (幻灯片布局类型枚举（两列文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-40.png)
                    标题、文字在左、文字在右
                </td>
            </tr>
            <tr>
                <td>
                    twoObj (两个物体)
                </td>
                <td>
                    ![img](./imgs/19pml-41.png)
                    标题、左侧对象、右侧对象
                </td>
            </tr>
            <tr>
                <td>
                    twoObjAndObj (两个对象和对象)
                </td>
                <td>
                    ![img](./imgs/19pml-42.png)
                    标题，左侧两个对象，右侧一个对象
                </td>
            </tr>
            <tr>
                <td>
                    twoObjAndTx (两个对象和文本) 
                </td>
                <td>
                    ![img](./imgs/19pml-43.png)
                    标题，左侧两个对象，右侧文本
                </td>
            </tr>
            <tr>
                <td>
                    twoObjOverTx (文本上的两个对象) 
                </td>
                <td>
                    ![img](./imgs/19pml-44.png)
                    标题，两个对象在顶部，文本在底部
                </td>
            </tr>
            <tr>
                <td>
                    twoTxTwoObj (两个文本和两个对象)
                </td>
                <td>
                    ![img](./imgs/19pml-45.png)
                    标题，两个对象，每个对象都有文本
                </td>
            </tr>
            <tr>
                <td>
                    tx (幻灯片布局类型枚举（文本）) 
                </td>
                <td>
                    ![img](./imgs/19pml-46.png)
                    标题和文字
                </td>
            </tr>
            <tr>
                <td>
                    txAndChart (幻灯片布局类型枚举（文本和图表）)
                </td>
                <td>
                    ![img](./imgs/19pml-47.png)
                    标题、文字在左边，图表在右边
                </td>
            </tr>
            <tr>
                <td>
                    txAndClipArt (文本和剪贴画) 
                </td>
                <td>
                    ![img](./imgs/19pml-48.png)
                    标题、文字在左，剪贴画在右
                </td>
            </tr>
            <tr>
                <td>
                    txAndMedia (幻灯片布局类型枚举（文本和媒体）)
                </td>
                <td>
                    ![img](./imgs/19pml-49.png)
                    标题、文字在左，媒体在右
                </td>
            </tr>
            <tr>
                <td>
                    txAndObj (幻灯片布局类型枚举（文本和对象）)
                </td>
                <td>
                    ![img](./imgs/19pml-50.png)
                    标题、文字在左，对象在右
                </td>
            </tr>
            <tr>
                <td>
                    txAndTwoObj (文本和两个对象)
                </td>
                <td>
                    ![img](./imgs/19pml-51.png)
                    标题、文本在左侧，两个对象在右侧
                </td>
            </tr>
            <tr>
                <td>
                    txOverObj (幻灯片布局类型枚举（对象上的文本）)
                </td>
                <td>
                    ![img](./imgs/19pml-52.png)
                    标题、文本在顶部，对象在底部
                </td>
            </tr>
            <tr>
                <td>
                    vertTitleAndTx (垂直标题和文本)
                </td>
                <td>
                    ![img](./imgs/19pml-53.png)
                    右侧垂直标题，左侧垂直文本
                </td>
            </tr>
            <tr>
                <td>
                    vertTitleAndTxOverChart (图表上的垂直标题和文本)
                </td>
                <td>
                    ![img](./imgs/19pml-54.png)
                    垂直标题在右侧，垂直文本在顶部，图表在底部
                </td>
            </tr>
            <tr>
                <td>
                    vertTx (竖排文字)
                </td>
                <td>
                    ![img](./imgs/19pml-55.png)
                    标题和垂直文本正文
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_SlideLayoutType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideLayoutType (Slide Layout Type)**

    This simple type defines an arrangement of content on a slide. Each layout type is not tied to an exact positioning of placeholders, but rather provides a higher-level description of the content type and positioning of placeholders. This information can be used by the application to aid in mapping between different layouts. The application can choose which, if any, of these layouts to make available through its user interface.
    
    Each layout contains zero or more placeholders, each with a specific content type. An "object" placeholder can contain any kind of data. Media placeholders are intended to hold video or audio clips. The enumeration value descriptions include illustrations of sample layouts for each value of the simple type.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    blank (Slide Layout Type Enumeration ( Blank ))
                </td>
                <td>
                    ![img](./imgs/19pml-21.png)
                    Blank
                </td>
            </tr>
            <tr>
                <td>
                    chart (Chart)
                </td>
                <td>
                    ![img](./imgs/19pml-22.png)
                    Title and chart
                </td>
            </tr>
            <tr>
                <td>
                    chartAndTx (Slide Layout Type Enumeration ( Chart and Text ))
                </td>
                <td>
                    ![img](./imgs/19pml-23.png)
                    Title, chart on left and text on right
                </td>
            </tr>
            <tr>
                <td>
                    clipArtAndTx (Clip Art and Text)
                </td>
                <td>
                    ![img](./imgs/19pml-24.png)
                    Title, clipart on left, text on right
                </td>
            </tr>
            <tr>
                <td>
                    clipArtAndVertTx (Clip Art and Vertical Text)
                </td>
                <td>
                    ![img](./imgs/19pml-25.png)
                    Title, clip art on left, vertical text on right
                </td>
            </tr>
            <tr>
                <td>
                    cust (Slide Layout Type Enumeration ( Custom ))
                </td>
                <td>
                    Custom layout defined by user
                </td>
            </tr>
            <tr>
                <td>
                    dgm (Slide Layout Type Enumeration ( Diagram ))
                </td>
                <td>
                    ![img](./imgs/19pml-26.png)
                    Title and diagram
                </td>
            </tr>
            <tr>
                <td>
                    fourObj (Four Objects)
                </td>
                <td>
                    ![img](./imgs/19pml-27.png)
                    Title and four objects
                </td>
            </tr>
            <tr>
                <td>
                    mediaAndTx (Slide Layout Type Enumeration ( Media and Text ))
                </td>
                <td>
                    ![img](./imgs/19pml-28.png)
                    Title and four objects
                </td>
            </tr>
            <tr>
                <td>
                    obj (Title and Object)
                </td>
                <td>
                    ![img](./imgs/19pml-29.png)
                    Title and object
                </td>
            </tr>
            <tr>
                <td>
                    objAndTwoObj (Object and Two Object)
                </td>
                <td>
                    ![img](./imgs/19pml-30.png)
                    Title, one object on left, two objects on right
                </td>
            </tr>
            <tr>
                <td>
                    objAndTx (Slide Layout Type Enumeration ( Object and Text ))
                </td>
                <td>
                    ![img](./imgs/19pml-31.png)
                    Title, object on left, text on right
                </td>
            </tr>
            <tr>
                <td>
                    objOnly (Object)
                </td>
                <td>
                    ![img](./imgs/19pml-32.png)
                    Object only
                </td>
            </tr>
            <tr>
                <td>
                    objOverTx (Slide Layout Type Enumeration ( Object over Text))
                </td>
                <td>
                    ![img](./imgs/19pml-33.png)
                    Title, object on top, text on bottom
                </td>
            </tr>
            <tr>
                <td>
                    objTx (Title, Object, and Caption)
                </td>
                <td>
                    ![img](./imgs/19pml-34.png)
                    Title, object and caption text
                </td>
            </tr>
            <tr>
                <td>
                    picTx (Picture and Caption)
                </td>
                <td>
                    ![img](./imgs/19pml-35.png)
                    Title, picture, and caption text
                </td>
            </tr>
            <tr>
                <td>
                    secHead (Section Header)
                </td>
                <td>
                    ![img](./imgs/19pml-36.png)
                    Section header title and subtitle text
                </td>
            </tr>
            <tr>
                <td>
                    tbl (Slide Layout Type Enumeration ( Table ))
                </td>
                <td>
                    ![img](./imgs/19pml-37.png)
                    Title and table
                </td>
            </tr>
            <tr>
                <td>
                    title (Slide Layout Type Enumeration ( Title ))
                </td>
                <td>
                    ![img](./imgs/19pml-38.png)
                    Title layout with centered title and subtitle placeholders
                </td>
            </tr>
            <tr>
                <td>
                    titleOnly (Slide Layout Type Enumeration ( Title Only ))
                </td>
                <td>
                    ![img](./imgs/19pml-39.png)
                    Title only
                </td>
            </tr>
            <tr>
                <td>
                    twoColTx (Slide Layout Type Enumeration ( Two Column Text ))
                </td>
                <td>
                    ![img](./imgs/19pml-40.png)
                    Title, text on left, text on right
                </td>
            </tr>
            <tr>
                <td>
                    twoObj (Two Objects)
                </td>
                <td>
                    ![img](./imgs/19pml-41.png)
                    Title, object on left, object on right
                </td>
            </tr>
            <tr>
                <td>
                    twoObjAndObj (Two Objects and Object)
                </td>
                <td>
                    ![img](./imgs/19pml-42.png)
                    Title, two objects on left, one object on right
                </td>
            </tr>
            <tr>
                <td>
                    twoObjAndTx (Two Objects and Text) 
                </td>
                <td>
                    ![img](./imgs/19pml-43.png)
                    Title, two objects on left, text on right
                </td>
            </tr>
            <tr>
                <td>
                    twoObjOverTx (Two Objects over Text) 
                </td>
                <td>
                    ![img](./imgs/19pml-44.png)
                    Title, two objects on top, text on bottom
                </td>
            </tr>
            <tr>
                <td>
                    twoTxTwoObj (Two Text and Two Objects)
                </td>
                <td>
                    ![img](./imgs/19pml-45.png)
                    Title, two objects each with text
                </td>
            </tr>
            <tr>
                <td>
                    tx (Slide Layout Type Enumeration ( Text )) 
                </td>
                <td>
                    ![img](./imgs/19pml-46.png)
                    Title and text
                </td>
            </tr>
            <tr>
                <td>
                    txAndChart (Slide Layout Type Enumeration ( Text and Chart ))
                </td>
                <td>
                    ![img](./imgs/19pml-47.png)
                    Title, text on left and chart on right
                </td>
            </tr>
            <tr>
                <td>
                    txAndClipArt (Text and Clip Art) 
                </td>
                <td>
                    ![img](./imgs/19pml-48.png)
                    Title, text on left, clip art on right
                </td>
            </tr>
            <tr>
                <td>
                    txAndMedia (Slide Layout Type Enumeration ( Text and Media ))
                </td>
                <td>
                    ![img](./imgs/19pml-49.png)
                    Title, text on left, media on right
                </td>
            </tr>
            <tr>
                <td>
                    txAndObj (Slide Layout Type Enumeration ( Text and Object ))
                </td>
                <td>
                    ![img](./imgs/19pml-50.png)
                    Title, text on left, object on right
                </td>
            </tr>
            <tr>
                <td>
                    txAndTwoObj (Text and Two Objects)
                </td>
                <td>
                    ![img](./imgs/19pml-51.png)
                    Title, text on left, two objects on right
                </td>
            </tr>
            <tr>
                <td>
                    txOverObj (Slide Layout Type Enumeration ( Text over Object))
                </td>
                <td>
                    ![img](./imgs/19pml-52.png)
                    Title, text on top, object on bottom
                </td>
            </tr>
            <tr>
                <td>
                    vertTitleAndTx (Vertical Title and Text)
                </td>
                <td>
                    ![img](./imgs/19pml-53.png)
                    Vertical title on right, vertical text on left
                </td>
            </tr>
            <tr>
                <td>
                    vertTitleAndTxOverChart (Vertical Title and Text Over Chart)
                </td>
                <td>
                    ![img](./imgs/19pml-54.png)
                    Vertical title on right, vertical text on top, chart on bottom
                </td>
            </tr>
            <tr>
                <td>
                    vertTx (Vertical Text)
                </td>
                <td>
                    ![img](./imgs/19pml-55.png)
                    Title and vertical text body
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideLayoutType) is located in §A.3. end note]

## 19.7.16 ST_SlideMasterId (幻灯片母版 ID)

=== "中文"

    此简单类型指定幻灯片母版标识符允许的编号。

    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 此简单类型的最小值大于或等于 2147483648。

    [Note: 此简单类型的内容模型 (ST_SlideMasterId) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideMasterId (Slide Master ID)**

    This simple type specifies the allowed numbering for the slide master identifier.

    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.

    This simple type also specifies the following restrictions:

    - This simple type has a minimum value of greater than or equal to 2147483648.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideMasterId) is located in §A.3. end note]

## 19.7.17 ST_SlideSizeCoordinate (幻灯片大小坐标)

=== "中文"

    此简单类型指定 EMU（英制公制单位）中的幻灯片大小坐标。

    此简单类型的内容是 ST_PositiveCooperative32 数据类型 (§20.1.10.43) 的限制。

    这个简单类型还指定了以下限制：

    - 此简单类型的最大值小于或等于 51206400。
    - 此简单类型的最小值大于或等于 914400。

    [Note: 此简单类型的内容模型 (ST_SlideSizeCooperative) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideSizeCoordinate (Slide Size Coordinate)**

    This simple type specifies the slide size coordinate in EMUs (English Metric Units).
    
    This simple type's contents are a restriction of the ST_PositiveCoordinate32 datatype (§20.1.10.43).

    This simple type also specifies the following restrictions:

    - This simple type has a maximum value of less than or equal to 51206400.
    - This simple type has a minimum value of greater than or equal to 914400.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideSizeCoordinate) is located in §A.3. end note]

## 19.7.18 ST_SlideSi zeType (幻灯片尺寸类型)

=== "中文"

    此简单类型指定应优化幻灯片的幻灯片大小类型。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    35mm (35mm Film)
                </td>
                <td>
                    应针对 35 毫米胶片输出优化幻灯片尺寸
                </td>
            </tr>
            <tr>
                <td>
                    A3 (A3) 
                </td>
                <td>
                    应针对 A3 输出优化幻灯片尺寸
                </td>
            </tr>
            <tr>
                <td>
                    A4 (A4)
                </td>
                <td>
                    应针对 A4 输出优化幻灯片尺寸
                </td>
            </tr>
            <tr>
                <td>
                    B4ISO (B4ISO)
                </td>
                <td>
                    应针对 B4ISO 输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    B4JIS (B4JIS)
                </td>
                <td>
                    应针对 B4JIS 输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    B5ISO (B5ISO)
                </td>
                <td>
                    应针对 B5ISO 输出优化幻灯片尺寸
                </td>
            </tr>
            <tr>
                <td>
                    B5JIS (B5JIS) 
                </td>
                <td>
                    应针对 B5JIS 输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    banner (Banner) 
                </td>
                <td>
                    应针对横幅输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    custom (Custom) 
                </td>
                <td>
                    应针对自定义输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    hagakiCard (Hagaki Card) 
                </td>
                <td>
                    应针对 hagaki 卡输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    ledger (Ledger) 
                </td>
                <td>
                    应针对账本输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    letter (Letter) 
                </td>
                <td>
                    应针对字母输出优化幻灯片大小
                </td>
            </tr>
            <tr>
                <td>
                    overhead (Overhead) 
                </td>
                <td>
                    幻灯片大小应针对开销输出进行优化
                </td>
            </tr>
            <tr>
                <td>
                    screen16x10 (Screen 16x10)
                </td>
                <td>
                    幻灯片大小应针对 16x10 屏幕输出进行优化
                </td>
            </tr>
            <tr>
                <td>
                    screen16x9 (Screen 16x9)  
                </td>
                <td>
                    幻灯片大小应针对 16x9 屏幕输出进行优化
                </td>
            </tr>
            <tr>
                <td>
                    screen4x3 (Screen 4x3) 
                </td>
                <td>
                    幻灯片大小应针对 4x3 屏幕输出进行优化
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_SlideSizeType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_SlideSizeType (Slide Size Type)**

    This simple type specifies the kind of slide size that the slide should be optimized for.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    35mm (35mm Film)
                </td>
                <td>
                    Slide size should be optimized for 35mm film output
                </td>
            </tr>
            <tr>
                <td>
                    A3 (A3) 
                </td>
                <td>
                    Slide size should be optimized for A3 output
                </td>
            </tr>
            <tr>
                <td>
                    A4 (A4)
                </td>
                <td>
                    Slide size should be optimized for A4 output
                </td>
            </tr>
            <tr>
                <td>
                    B4ISO (B4ISO)
                </td>
                <td>
                    Slide size should be optimized for B4ISO output
                </td>
            </tr>
            <tr>
                <td>
                    B4JIS (B4JIS)
                </td>
                <td>
                    Slide size should be optimized for B4JIS output
                </td>
            </tr>
            <tr>
                <td>
                    B5ISO (B5ISO)
                </td>
                <td>
                    Slide size should be optimized for B5ISO output
                </td>
            </tr>
            <tr>
                <td>
                    B5JIS (B5JIS) 
                </td>
                <td>
                    Slide size should be optimized for B5JIS output
                </td>
            </tr>
            <tr>
                <td>
                    banner (Banner) 
                </td>
                <td>
                    Slide size should be optimized for banner output
                </td>
            </tr>
            <tr>
                <td>
                    custom (Custom) 
                </td>
                <td>
                    Slide size should be optimized for custom output
                </td>
            </tr>
            <tr>
                <td>
                    hagakiCard (Hagaki Card) 
                </td>
                <td>
                    Slide size should be optimized for hagaki card output
                </td>
            </tr>
            <tr>
                <td>
                    ledger (Ledger) 
                </td>
                <td>
                    Slide size should be optimized for ledger output
                </td>
            </tr>
            <tr>
                <td>
                    letter (Letter) 
                </td>
                <td>
                    Slide size should be optimized for letter output
                </td>
            </tr>
            <tr>
                <td>
                    overhead (Overhead) 
                </td>
                <td>
                    Slide size should be optimized for overhead output
                </td>
            </tr>
            <tr>
                <td>
                    screen16x10 (Screen 16x10)
                </td>
                <td>
                    Slide size should be optimized for 16x10 screen output
                </td>
            </tr>
            <tr>
                <td>
                    screen16x9 (Screen 16x9)  
                </td>
                <td>
                    Slide size should be optimized for 16x9 screen output
                </td>
            </tr>
            <tr>
                <td>
                    screen4x3 (Screen 4x3) 
                </td>
                <td>
                    Slide size should be optimized for 4x3 screen output
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SlideSizeType) is located in §A.3. end note]

## 19.7.19 ST_SplitterBarState (分离条状态)

=== "中文"

    此简单类型指定分隔条应显示的状态。分隔条将查看区域内的主要区域和次要区域分开。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    maximized (Max)
                </td>
                <td>
                    主要区域占据应用程序允许的最大查看区域。
                </td>
            </tr>
            <tr>
                <td>
                    minimized (Min)
                </td>
                <td>
                    主要区域占据应用程序允许的最小查看区域。
                </td>
            </tr>
            <tr>
                <td>
                    restored (Restored)
                </td>
                <td>
                    主要区域具有特定的中间尺寸。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_SplitterBarState) 的 W3C XML 架构定义位于 §A.3. end note]

=== "英文"

    **ST_SplitterBarState (Splitter Bar State)**

    This simple type specifies the state that the splitter bar should be shown in. The splitter bar separates a primary and secondary region within a viewing area.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    maximized (Max)
                </td>
                <td>
                    The primary region occupies the greatest amount of the viewing area allowed by the application.
                </td>
            </tr>
            <tr>
                <td>
                    minimized (Min)
                </td>
                <td>
                    The primary region occupies the least amount of the viewing area allowed by the application.
                </td>
            </tr>
            <tr>
                <td>
                    restored (Restored)
                </td>
                <td>
                    The primary region has a specific intermediate size. 
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_SplitterBarState) is located in §A.3. end note]

## 19.7.20 ST_TLAnimateBehaviorCalcMode (时间列表动画行为计算模式)

=== "中文"

    这个简单的类型指定动画如何从一个点流动到另一个点。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    discrete (Calc Mode Enum ( Discrete ))
                </td>
                <td>
                    描述
                </td>
            </tr>
            <tr>
                <td>
                    fmla (Calc Mode Enum ( Formula ))
                </td>
                <td>
                    公式
                </td>
            </tr>
            <tr>
                <td>
                    lin (Calc Mode Enum ( Linear ))
                </td>
                <td>
                    线性
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateBehaviorCalcMode) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateBehaviorCalcMode (Time List Animate Behavior Calculate Mode)**

    This simple type specifies how the animation flows from point to point.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    discrete (Calc Mode Enum ( Discrete ))
                </td>
                <td>
                    Descrete
                </td>
            </tr>
            <tr>
                <td>
                    fmla (Calc Mode Enum ( Formula ))
                </td>
                <td>
                    Formula
                </td>
            </tr>
            <tr>
                <td>
                    lin (Calc Mode Enum ( Linear ))
                </td>
                <td>
                    Linear
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateBehaviorCalcMode) is located in §A.3. end note]

## 19.7.21 ST_TLAnimateBehaviorValueType (时间列表动画行为值类型)

=== "中文"

    这个简单类型指定属性值的类型。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    clr (Value Type Enum ( Color ))
                </td>
                <td>
                    颜色
                </td>
            </tr>
            <tr>
                <td>
                    num (Value Type Enum ( Number ))
                </td>
                <td>
                    数字
                </td>
            </tr>
            <tr>
                <td>
                    str (Value Type Enum ( String ))
                </td>
                <td>
                    字符串
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateBehaviorValueType) is located in §A.3. end note]

=== "英文"

    **ST_TLAnimateBehaviorValueType (Time List Animate Behavior Value Types)**

    This simple type specifies the type of property value.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    clr (Value Type Enum ( Color ))
                </td>
                <td>
                    Color
                </td>
            </tr>
            <tr>
                <td>
                    num (Value Type Enum ( Number ))
                </td>
                <td>
                    Number
                </td>
            </tr>
            <tr>
                <td>
                    str (Value Type Enum ( String ))
                </td>
                <td>
                    String
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateBehaviorValueType) is located in §A.3. end note]

## 19.7.22 ST_TLAnimateColorDirection (时间列表动画颜色方向)

=== "中文"

    此简单类型指定插入动画的方向（顺时针或逆时针）。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    ccw (Counter-Clockwise) 
                </td>
                <td>
                    逆时针
                </td>
            </tr>
            <tr>
                <td>
                    cw (Direction Enum ( Clockwise ))
                </td>
                <td>
                    顺时针
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateColorDirection) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateColorDirection (Time List Animate Color Direction)**

    This simple type specifies the direction in which to interpolate the animation (clockwise or counterclockwise).

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    ccw (Counter-Clockwise) 
                </td>
                <td>
                    Counter-Clockwise
                </td>
            </tr>
            <tr>
                <td>
                    cw (Direction Enum ( Clockwise ))
                </td>
                <td>
                    Clockwise
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateColorDirection) is located in §A.3. end note]

## 19.7.23 ST_TLAnimateColorSpace (时间列表动画色彩空间)

=== "中文"

    这个简单的类型指定动画的色彩空间。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    hsl (Color Space Enum ( HSL ))
                </td>
                <td>
                    色相、饱和度、亮度
                </td>
            </tr>
            <tr>
                <td>
                    rgb (Color Space Enum ( RGB ))
                </td>
                <td>
                    红、绿、蓝
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateColorSpace) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateColorSpace (Time List Animate Color Space)**

    This simple type specifies the color space of the animation.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    hsl (Color Space Enum ( HSL ))
                </td>
                <td>
                    Hue, Saturation, Luminance
                </td>
            </tr>
            <tr>
                <td>
                    rgb (Color Space Enum ( RGB ))
                </td>
                <td>
                    Red, Green, Blue
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateColorSpace) is located in §A.3. end note]

## 19.7.24 ST_TLAnimateEffectTransition (时间列表动画效果过渡)

=== "中文"

    这个简单类型指定效果是过渡入、过渡出还是两者都不是。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    in (Transition Enum ( In ))
                </td>
                <td>
                    进入
                </td>
            </tr>
            <tr>
                <td>
                    none (Transition Enum ( None ))
                </td>
                <td>
                    无
                </td>
            </tr>
            <tr>
                <td>
                    out (Transition Enum ( Out ))
                </td>
                <td>
                    退出
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateEffectTransition) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateEffectTransition (Time List Animate Effect Transition)**

    This simple type specifies whether the effect is a transition in, transition out, or neither.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    in (Transition Enum ( In ))
                </td>
                <td>
                    In
                </td>
            </tr>
            <tr>
                <td>
                    none (Transition Enum ( None ))
                </td>
                <td>
                    None
                </td>
            </tr>
            <tr>
                <td>
                    out (Transition Enum ( Out ))
                </td>
                <td>
                    Out
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateEffectTransition) is located in §A.3. end note]

## 19.7.25 ST_TLAnimateMotionBehaviorOrigin (时间列表动画动作行为起源)

=== "中文"

    这个简单的类型指定运动路径的原点相对于什么。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    layout (Origin Enum ( Layout ))
                </td>
                <td>
                    Layout
                </td>
            </tr>
            <tr>
                <td>
                    parent (Origin Enum ( Parent )) 
                </td>
                <td>
                    Parent
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateMotionBehaviorOrigin) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateMotionBehaviorOrigin (Time List Animate Motion Behavior Origin)**

    This simple type specifies what the origin of the motion path is relative to.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    layout (Origin Enum ( Layout ))
                </td>
                <td>
                    Layout
                </td>
            </tr>
            <tr>
                <td>
                    parent (Origin Enum ( Parent )) 
                </td>
                <td>
                    Parent
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateMotionBehaviorOrigin) is located in §A.3. end note]

## 19.7.26 ST_TLAnimateMotionPathEditMode (时间列表动画运动路径编辑模式)

=== "中文"

    这个简单类型指定当目标元素移动时运动路径如何移动。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    fixed (Path Edit Mode Enum ( Fixed ))
                </td>
                <td>
                    固定的
                </td>
            </tr>
            <tr>
                <td>
                    relative (Path Edit Mode Enum ( Relative ))
                </td>
                <td>
                    相对的
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLAnimateMotionPathEditMode) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLAnimateMotionPathEditMode (Time List Animate Motion Path Edit Mode)**

    This simple type specifies how the motion path moves when the target element is moved.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    fixed (Path Edit Mode Enum ( Fixed ))
                </td>
                <td>
                    Fixed
                </td>
            </tr>
            <tr>
                <td>
                    relative (Path Edit Mode Enum ( Relative ))
                </td>
                <td>
                    Relative
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLAnimateMotionPathEditMode) is located in §A.3. end note]

## 19.7.27 ST_TLBehaviorAccumulateType (行为累积型)

=== "中文"

    当设置为“始终”时，这种简单的类型会在每次迭代时构建重复的动画。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    always (Accumulate Enum ( Always ))
                </td>
                <td>
                    总是
                </td>
            </tr>
            <tr>
                <td>
                    none (Accumulate Enum ( None ))
                </td>
                <td>
                    无
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLBehaviorAccumulateType) 的 W3C XML 架构定义位于 §A.3. end note]

=== "英文"

    **ST_TLBehaviorAccumulateType (Behavior Accumulate Type)**

    This simple type makes a repeating animation build with each iteration when set to "always."

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    always (Accumulate Enum ( Always ))
                </td>
                <td>
                    Always
                </td>
            </tr>
            <tr>
                <td>
                    none (Accumulate Enum ( None ))
                </td>
                <td>
                    None
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLBehaviorAccumulateType) is located in §A.3. end note]

## 19.7.28 ST_TLBehaviorAdditiveType (行为添加剂类型)

=== "中文"

    这个简单类型指定如何将动画值应用到属性的原始值。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    base (Additive Enum ( Base )) 
                </td>
                <td>
                    基础
                </td>
            </tr>
            <tr>
                <td>
                    mult (Additive Enum ( Multiply )) 
                </td>
                <td>
                    乘
                </td>
            </tr>
            <tr>
                <td>
                    none (None) 
                </td>
                <td>
                    无
                </td>
            </tr>
            <tr>
                <td>
                    repl (Additive Enum ( Replace )) 
                </td>
                <td>
                    替换
                </td>
            </tr>
            <tr>
                <td>
                    sum (Additive Enum ( Sum )) 
                </td>
                <td>
                    和
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLBehaviorAdditiveType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLBehaviorAdditiveType (Behavior Additive Type)**

    This simple type specifies how to apply the animation values to the original value for the property.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    base (Additive Enum ( Base )) 
                </td>
                <td>
                    Base
                </td>
            </tr>
            <tr>
                <td>
                    mult (Additive Enum ( Multiply )) 
                </td>
                <td>
                    Multiply
                </td>
            </tr>
            <tr>
                <td>
                    none (None) 
                </td>
                <td>
                    None
                </td>
            </tr>
            <tr>
                <td>
                    repl (Additive Enum ( Replace )) 
                </td>
                <td>
                    Replace
                </td>
            </tr>
            <tr>
                <td>
                    sum (Additive Enum ( Sum )) 
                </td>
                <td>
                    Sum
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLBehaviorAdditiveType) is located in §A.3. end note]

## 19.7.29 ST_TLBehaviorOverrideType (行为覆盖类型)

=== "中文"

    这个简单类型指定行为应如何覆盖目标元素上动画的属性值。 “childStyle”清除目标元素中包含的子元素的属性。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    childStyle (Override Enum ( Child Style ))
                </td>
                <td>
                    子元素风格
                </td>
            </tr>
            <tr>
                <td>
                    normal (Override Enum ( Normal ))
                </td>
                <td>
                    常规
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLBehaviorOverrideType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLBehaviorOverrideType (Behavior Override Type)**

    This simple type specifies how a behavior should override values of the attribute being animated on the target element. The "childStyle" clears the attributes on the children contained inside the target element.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    childStyle (Override Enum ( Child Style ))
                </td>
                <td>
                    Child Style
                </td>
            </tr>
            <tr>
                <td>
                    normal (Override Enum ( Normal ))
                </td>
                <td>
                    Normal
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLBehaviorOverrideType) is located in §A.3. end note]

## 19.7.30 ST_TLBehaviorTransformType (行为转变类型)

=== "中文"

    这个简单类型指定行为如何为目标元素设置动画。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    img (Image)
                </td>
                <td>
                    图像变换
                </td>
            </tr>
            <tr>
                <td>
                    pt (Point) 
                </td>
                <td>
                    点变换
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLBehaviorTransformType) is located in §A.3. end note]

=== "英文"

    **ST_TLBehaviorTransformType (Behavior Transform Type)**

    This simple type specifies how the behavior animates the target element.

    This simple type's contents are a restriction of the W3C XML Schema token datatype

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
                <td>
                    img (Image)
                </td>
                <td>
                    Image transform
                </td>
            </tr>
            <tr>
                <td>
                    pt (Point) 
                </td>
                <td>
                    Point transform
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLBehaviorTransformType) is located in §A.3. end note]

## 19.7.31 ST_TLChartSubelementType (图表子元素类型)

=== "中文"

    此简单类型定义由图表的子元素表示的动画目标元素。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    category (类别轴) 
                </td>
                <td>
                    类别
                </td>
            </tr>
            <tr>
                <td>
                    gridLegend (网格图例) 
                </td>
                <td>
                    背景元素（网格和图例）
                </td>
            </tr>
            <tr>
                <td>
                    ptInCategory (类别中的单点) 
                </td>
                <td>
                    类别元素
                </td>
            </tr>
            <tr>
                <td>
                    ptInSeries (数据系列中的单点)
                </td>
                <td>
                    系列元素
                </td>
            </tr>
            <tr>
                <td>
                    series (数据系列)
                </td>
                <td>
                    系列
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLChartSubelementType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLChartSubelementType (Chart Subelement Type)**

    This simple type defines an animation target element that is represented by a subelement of a chart.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    category (Category Axis) 
                </td>
                <td>
                    Category
                </td>
            </tr>
            <tr>
                <td>
                    gridLegend (Grid Legend) 
                </td>
                <td>
                    Background Element (Grid and Legend)
                </td>
            </tr>
            <tr>
                <td>
                    ptInCategory (Single Point in Category) 
                </td>
                <td>
                    Category Element
                </td>
            </tr>
            <tr>
                <td>
                    ptInSeries (Single Point in Data Series)
                </td>
                <td>
                    Series Element
                </td>
            </tr>
            <tr>
                <td>
                    series (Data Series)
                </td>
                <td>
                    Series
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLChartSubelementType) is located in §A.3. end note]

## 19.7.32 ST_TLCommandType (图表子元素类型)

=== "中文"

    这个简单类型指定命令类型。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    call (命令类型枚举 ( Call ))
                </td>
                <td>
                    调用
                </td>
            </tr>
            <tr>
                <td>
                    evt (命令类型枚举 ( Event ))
                </td>
                <td>
                    事件
                </td>
            </tr>
            <tr>
                <td>
                    verb (命令类型枚举 ( Verb ))
                </td>
                <td>
                    变量
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLCommandType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLCommandType (Command Type)**

    This simple type specifies a command type.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    call (Command Type Enum ( Call ))
                </td>
                <td>
                    Call
                </td>
            </tr>
            <tr>
                <td>
                    evt (Command Type Enum ( Event ))
                </td>
                <td>
                    Event
                </td>
            </tr>
            <tr>
                <td>
                    verb (Command Type Enum ( Verb ))
                </td>
                <td>
                    Verb
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLCommandType) is located in §A.3. end note]

## 19.7.33 ST_TLDiagramBuildType (图表构建类型)

=== "中文"

    这个简单的类型指定了不同的图表构建类型。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    allAtOnce (图构建类型枚举 ( All At Once )) 
                </td>
                <td>
                    一次全部
                </td>
            </tr>
            <tr>
                <td>
                    breadthByLvl (图构建类型枚举 ( Breadth By Level ))
                </td>
                <td>
                    Breadth By Level
                </td>
            </tr>
            <tr>
                <td>
                    breadthByNode (图构建类型枚举 ( Breadth By Node ))
                </td>
                <td>
                    Breadth By Node
                </td>
            </tr>
            <tr>
                <td>
                    ccw (图构建类型枚举 ( Counter-Clockwise )) 
                </td>
                <td>
                    Counter-Clockwise
                </td>
            </tr>
            <tr>
                <td>
                    ccwIn (图构建类型枚举 ( Counter-ClockwiseIn ))
                </td>
                <td>
                    Counter-Clockwise-In
                </td>
            </tr>
            <tr>
                <td>
                    ccwOut (图构建类型枚举 ( CounterClockwise-Out ))
                </td>
                <td>
                    Counter-Clockwise-Out
                </td>
            </tr>
            <tr>
                <td>
                    cust (图构建类型枚举 ( Custom )) 
                </td>
                <td>
                    Custom
                </td>
            </tr>
            <tr>
                <td>
                    cw (图构建类型枚举 ( Clockwise )) 
                </td>
                <td>
                    Clockwise
                </td>
            </tr>
            <tr>
                <td>
                    cwIn (图构建类型枚举 ( Clockwise-In )) 
                </td>
                <td>
                    Clockwise-In
                </td>
            </tr>
            <tr>
                <td>
                    cwOut (图构建类型枚举 ( Clockwise-Out )) 
                </td>
                <td>
                    Clockwise-Out
                </td>
            </tr>
            <tr>
                <td>
                    depthByBranch (图构建类型枚举 ( Depth By Branch ))
                </td>
                <td>
                    Depth By Branch
                </td>
            </tr>
            <tr>
                <td>
                    depthByNode (图构建类型枚举 ( Depth By Node ))
                </td>
                <td>
                    Depth By Node
                </td>
            </tr>
            <tr>
                <td>
                    down (图构建类型枚举 ( Down )) 
                </td>
                <td>
                    Down
                </td>
            </tr>
            <tr>
                <td>
                    inByRing (图构建类型枚举 ( In-By-Ring )) 
                </td>
                <td>
                    In-By-Ring
                </td>
            </tr>
            <tr>
                <td>
                    outByRing (图构建类型枚举 ( Out-By-Ring )) 
                </td>
                <td>
                    Out-By-Ring
                </td>
            </tr>
            <tr>
                <td>
                    up (图构建类型枚举 ( Up ))
                </td>
                <td>
                    Up
                </td>
            </tr>
            <tr>
                <td>
                    whole (图构建类型枚举 ( Whole )) 
                </td>
                <td>
                    Whole
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLDiagramBuildType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLDiagramBuildType (Diagram Build Types)**

    This simple type specifies the different diagram build types.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    allAtOnce (Diagram Build Type Enum ( All At Once )) 
                </td>
                <td>
                    All At Once
                </td>
            </tr>
            <tr>
                <td>
                    breadthByLvl (Diagram Build Type Enum ( Breadth By Level ))
                </td>
                <td>
                    Breadth By Level
                </td>
            </tr>
            <tr>
                <td>
                    breadthByNode (Diagram Build Type Enum ( Breadth By Node ))
                </td>
                <td>
                    Breadth By Node
                </td>
            </tr>
            <tr>
                <td>
                    ccw (Diagram Build Type Enum ( Counter-Clockwise )) 
                </td>
                <td>
                    Counter-Clockwise
                </td>
            </tr>
            <tr>
                <td>
                    ccwIn (Diagram Build Type Enum ( Counter-ClockwiseIn ))
                </td>
                <td>
                    Counter-Clockwise-In
                </td>
            </tr>
            <tr>
                <td>
                    ccwOut (Diagram Build Type Enum ( CounterClockwise-Out ))
                </td>
                <td>
                    Counter-Clockwise-Out
                </td>
            </tr>
            <tr>
                <td>
                    cust (Diagram Build Type Enum ( Custom )) 
                </td>
                <td>
                    Custom
                </td>
            </tr>
            <tr>
                <td>
                    cw (Diagram Build Type Enum ( Clockwise )) 
                </td>
                <td>
                    Clockwise
                </td>
            </tr>
            <tr>
                <td>
                    cwIn (Diagram Build Type Enum ( Clockwise-In )) 
                </td>
                <td>
                    Clockwise-In
                </td>
            </tr>
            <tr>
                <td>
                    cwOut (Diagram Build Type Enum ( Clockwise-Out )) 
                </td>
                <td>
                    Clockwise-Out
                </td>
            </tr>
            <tr>
                <td>
                    depthByBranch (Diagram Build Type Enum ( Depth By Branch ))
                </td>
                <td>
                    Depth By Branch
                </td>
            </tr>
            <tr>
                <td>
                    depthByNode (Diagram Build Type Enum ( Depth By Node ))
                </td>
                <td>
                    Depth By Node
                </td>
            </tr>
            <tr>
                <td>
                    down (Diagram Build Type Enum ( Down )) 
                </td>
                <td>
                    Down
                </td>
            </tr>
            <tr>
                <td>
                    inByRing (Diagram Build Type Enum ( In-By-Ring )) 
                </td>
                <td>
                    In-By-Ring
                </td>
            </tr>
            <tr>
                <td>
                    outByRing (Diagram Build Type Enum ( Out-By-Ring )) 
                </td>
                <td>
                    Out-By-Ring
                </td>
            </tr>
            <tr>
                <td>
                    up (Diagram Build Type Enum ( Up ))
                </td>
                <td>
                    Up
                </td>
            </tr>
            <tr>
                <td>
                    whole (Diagram Build Type Enum ( Whole )) 
                </td>
                <td>
                    Whole
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLDiagramBuildType) is located in §A.3. end note]

## 19.7.34 ST_TLNextActionType (下一个操作类型)

=== "中文"

    这个简单的类型指定了按顺序前进时要执行的操作。 当值为“seek”时，它会在前进到下一个元素之前搜索当前子元素到其自然结束时间。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
 
    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    none (下一个操作类型枚举 ( None )) 
                </td>
                <td>
                    无
                </td>
            </tr>
            <tr>
                <td>
                    seek (下一个操作类型枚举 ( Seek ))
                </td>
                <td>
                    Seek
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLNextActionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLNextActionType (Next Action Type)**

    This simple type specifies what to do when going forward in a sequence. When the value is "seek," it seeks the current child element to its natural end time before advancing to the next element.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    none (Next Action Type Enum ( None )) 
                </td>
                <td>
                    None
                </td>
            </tr>
            <tr>
                <td>
                    seek (Next Action Type Enum ( Seek ))
                </td>
                <td>
                    Seek
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLNextActionType) is located in §A.3. end note]

## 19.7.35 ST_TLOleChartBuildType (嵌入式图表构建类型)

=== "中文"

    这个简单的类型描述了如何构建嵌入式图表。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    allAtOnce (图表构建类型枚举 ( All At Once )) 
                </td>
                <td>
                    一次全部
                </td>
            </tr>
            <tr>
                <td>
                    category (图表构建类型枚举 ( Category )) 
                </td>
                <td>
                    按类别
                </td>
            </tr>
            <tr>
                <td>
                    categoryEl (图表构建类型枚举 ( Category Element ))
                </td>
                <td>
                    按类别元素
                </td>
            </tr>
            <tr>
                <td>
                    series (图表构建类型枚举 ( Series ))
                </td>
                <td>
                    按系列
                </td>
            </tr>
            <tr>
                <td>
                    seriesEl (图表构建类型枚举 ( Series Element ))
                </td>
                <td>
                    按系列元素
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLOleChartBuildType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLOleChartBuildType (Embedded Chart Build Type)**

    This simple type describes how to build an embedded Chart.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    allAtOnce (Chart Build Type Enum ( All At Once )) 
                </td>
                <td>
                    All At Once
                </td>
            </tr>
            <tr>
                <td>
                    category (Chart Build Type Enum ( Category )) 
                </td>
                <td>
                    By Category
                </td>
            </tr>
            <tr>
                <td>
                    categoryEl (Chart Build Type Enum ( Category Element ))
                </td>
                <td>
                    By Category Element
                </td>
            </tr>
            <tr>
                <td>
                    series (Chart Build Type Enum ( Series ))
                </td>
                <td>
                    By Series
                </td>
            </tr>
            <tr>
                <td>
                    seriesEl (Chart Build Type Enum ( Series Element ))
                </td>
                <td>
                    By Series Element
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLOleChartBuildType) is located in §A.3. end note]

## 19.7.36 ST_TLParaBuildType (段落构建类型)

=== "中文"

    这个简单的类型描述了如何构建段落。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    allAtOnce (一次全部) 
                </td>
                <td>
                    指定一次为所有段落设置动画。
                </td>
            </tr>
            <tr>
                <td>
                    cust (自定义) 
                </td>
                <td>
                    指定构建具有自定义用户设置。
                </td>
            </tr>
            <tr>
                <td>
                    p (段落) 
                </td>
                <td>
                    指定对按项目符号级别分组的段落进行动画处理。
                </td>
            </tr>
            <tr>
                <td>
                    whole (整个) 
                </td>
                <td>
                    指定将整个文本正文作为一个块进行动画处理。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLParaBuildType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLParaBuildType (Paragraph Build Type)**

    This simple type describes how to build a paragraph.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    allAtOnce (All At Once) 
                </td>
                <td>
                    Specifies to animate all paragraphs at once.
                </td>
            </tr>
            <tr>
                <td>
                    cust (Custom) 
                </td>
                <td>
                    Specifies the build has custom user settings.
                </td>
            </tr>
            <tr>
                <td>
                    p (Paragraph) 
                </td>
                <td>
                    Specifies to animate paragraphs grouped by bullet level.
                </td>
            </tr>
            <tr>
                <td>
                    whole (Whole) 
                </td>
                <td>
                    Specifies to animate the entire body of text as one block.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLParaBuildType) is located in §A.3. end note]

## 19.7.37 ST_TLPreviousActionType (先前的操作类型)

=== "中文"

    这个简单的类型指定了按顺序倒退时要执行的操作。 当值为“skipTimed”时，序列继续向后移动，直到到达定义为仅出现在“下一个”事件上的序列元素。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    none (上一个操作类型枚举 ( None )) 
                </td>
                <td>
                    无
                </td>
            </tr>
            <tr>
                <td>
                    skipTimed (上一个操作类型枚举 ( Skip Timed )) 
                </td>
                <td>
                    跳过定时
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLPreviousActionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLPreviousActionType (Previous Action Type)**

    This simple type specifies what to do when going backwards in a sequence. When the value is "skipTimed," the sequence continues to go backwards until it reaches a sequence element that was defined to being only on a "next" event.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    none (Previous Action Type Enum ( None )) 
                </td>
                <td>
                    None
                </td>
            </tr>
            <tr>
                <td>
                    skipTimed (Previous Action Type Enum ( Skip Timed )) 
                </td>
                <td>
                    Skip Timed
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLPreviousActionType) is located in §A.3. end note]

## 19.7.38 ST_TLTime (Time)

=== "中文"

    这个简单的类型指定时间，在该时间之后自动将构建推进到下一步。 一段时间，以毫秒为单位。
    
    这个简单类型是以下类型的联合：
    
    - ST_TLTimeIndefinite 简单类型 (§19.7.40)。
    - W3C XML 架构 unsignedInt 数据类型。
    
    [Note: 此简单类型的内容模型 (ST_TLTime) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTime (时间)**

    This simple type specifies time after which to automatically advance the build to the next step. An amount of time, in milliseconds.
    
    This simple type is a union of the following types:
    
    - The ST_TLTimeIndefinite simple type (§19.7.40).
    - The W3C XML Schema unsignedInt datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTime) is located in §A.3. end note]

## 19.7.39 ST_TLTimeAnimateValueTime (动画时间)

=== "中文"

    这个简单类型指定元素时间跨度内的百分比。 不定值意味着应忽略该属性。

    这个简单类型是以下类型的联合：
    
    - ST_PositiveFixedPercentage 简单类型 (§20.1.10.45)。
    - ST_TLTimeIndefinite 简单类型 (§19.7.40)。
    
    [Note: 此简单类型的内容模型 (ST_TLTimeAnimateValueTime) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeAnimateValueTime (Animation Time)**

    This simple type specifies a percentage within the time span of the element. A value of indefinite means the attribute should be ignored.

    This simple type is a union of the following types:
    
    - The ST_PositiveFixedPercentage simple type (§20.1.10.45).
    - The ST_TLTimeIndefinite simple type (§19.7.40).
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeAnimateValueTime) is located in §A.3. end note]

## 19.7.40 ST_TLTimeIndefinite (无限期声明)

=== "中文"

    这个简单类型指定一个值，该值指定“不确定”的时间量——通常意味着该属性从属于其他已定义的属性。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    indefinite (不定类型枚举) 
                </td>
                <td>
                    指定不定时间
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeIndefinite) is located in §A.3. end note]

=== "英文"

    **ST_TLTimeIndefinite (Indefinite Time Declaration)**

    This simple type specifies a value that designates an "indefinite" amount time -- typically means this property is subordinate to other, defined properties.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    indefinite (Indefinite Type Enum) 
                </td>
                <td>
                    Specifies Indefinite Time
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeIndefinite) is located in §A.3. end note]

## 19.7.41 ST_TLTimeNodeFillType (时间节点填充类型)

=== "中文"

    这个简单类型指定当效果结束时效果对目标元素的属性留下哪些修改。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    freeze (Freeze) 
                </td>
                <td>
                    Freeze
                </td>
            </tr>
            <tr>
                <td>
                    hold (TimeNode Fill Type Enum ( Hold )) 
                </td>
                <td>
                    Hold
                </td>
            </tr>
            <tr>
                <td>
                    remove (Remove) 
                </td>
                <td>
                    Remove
                </td>
            </tr>
            <tr>
                <td>
                    transition (Transition) 
                </td>
                <td>
                    Transition
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodeFillType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeFillType (Time Node Fill Type)**

    This simple type specifies what modifications the effect leaves on the target element's properties when the effect ends.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    freeze (Freeze) 
                </td>
                <td>
                    Freeze
                </td>
            </tr>
            <tr>
                <td>
                    hold (TimeNode Fill Type Enum ( Hold )) 
                </td>
                <td>
                    Hold
                </td>
            </tr>
            <tr>
                <td>
                    remove (Remove) 
                </td>
                <td>
                    Remove
                </td>
            </tr>
            <tr>
                <td>
                    transition (Transition) 
                </td>
                <td>
                    Transition
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeFillType) is located in §A.3. end note]

## 19.7.42 ST_TLTimeNodeID (时间节点ID)

=== "中文"

    这种简单类型通过其标识符表示时间线上的节点或事件。

    此简单类型的内容是 W3C XML Schema unsignedInt 数据类型的限制。
    
    [Note: 此简单类型的内容模型 (ST_TLTimeNodeID) 的 W3C XML 架构定义位于§A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeID (Time Node ID)**

    This simple type represents a node or event on the timeline by its identifier.
    
    This simple type's contents are a restriction of the W3C XML Schema unsignedInt datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeID) is located in§A.3. end note]

## 19.7.43 ST_TLTimeNodeMasterRelation (时间节点主关系)

=== "中文"

    此简单类型指定时间节点相对于其主时间节点的回放方式。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    lastClick (时间节点主关系枚举 ( Last Click ))
                </td>
                <td>
                    最后一次点击
                </td>
            </tr>
            <tr>
                <td>
                    lastClick (时间节点主关系枚举 ( Last Click ))
                </td>
                <td>
                    下一步单击
                </td>
            </tr>
            <tr>
                <td>
                    sameClick (时间节点主关系枚举 ( Same Click ))
                </td>
                <td>
                    相同的点击
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodeMasterRelation) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeMasterRelation (Time Node Master Relation)**

    This simple type specifies how the time node plays back relative to its master time node.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    lastClick (TimeNode Master Relation Enum ( Last Click ))
                </td>
                <td>
                    Last Click
                </td>
            </tr>
            <tr>
                <td>
                    lastClick (TimeNode Master Relation Enum ( Last Click ))
                </td>
                <td>
                    Next Click
                </td>
            </tr>
            <tr>
                <td>
                    sameClick (TimeNode Master Relation Enum ( Same Click ))
                </td>
                <td>
                    Same Click
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeMasterRelation) is located in §A.3. end note]

## 19.7.44 ST_TLTimeNodePresetClassType (时间节点预设类类型)

=== "中文"

    这个简单类型指定了该效果所属的效果类。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    emph (预设类型枚举 ( Emphasis ))
                </td>
                <td>
                    强调预设
                </td>
            </tr>
            <tr>
                <td>
                    entr (预设类型枚举 ( Entrance )) 
                </td>
                <td>
                    入口预设
                </td>
            </tr>
            <tr>
                <td>
                    exit (Exit) 
                </td>
                <td>
                    退出预设
                </td>
            </tr>
            <tr>
                <td>
                    mediacall (预设类型枚举 ( Media Call )) 
                </td>
                <td>
                    媒体通话预设
                </td>
            </tr>
            <tr>
                <td>
                    path (预设类型枚举 ( Path )) 
                </td>
                <td>
                    路径预设
                </td>
            </tr>
            <tr>
                <td>
                    verb (预设类型枚举 ( Verb )) 
                </td>
                <td>
                    动词预设
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodePresetClassType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodePresetClassType (Time Node Preset Class Type)**

    This simple type specifies the class of effect in which this effect belongs.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    emph (Preset Type Enum ( Emphasis ))
                </td>
                <td>
                    Emphasis Preset
                </td>
            </tr>
            <tr>
                <td>
                    entr (Preset Type Enum ( Entrance )) 
                </td>
                <td>
                    Entrance Preset
                </td>
            </tr>
            <tr>
                <td>
                    exit (Exit) 
                </td>
                <td>
                    Exit Preset
                </td>
            </tr>
            <tr>
                <td>
                    mediacall (Preset Type Enum ( Media Call )) 
                </td>
                <td>
                    Media Call Preset
                </td>
            </tr>
            <tr>
                <td>
                    path (Preset Type Enum ( Path )) 
                </td>
                <td>
                    Path Preset
                </td>
            </tr>
            <tr>
                <td>
                    verb (Preset Type Enum ( Verb )) 
                </td>
                <td>
                    Verb Preset
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodePresetClassType) is located in §A.3. end note]

## 19.7.45 ST_TLTimeNodeRestartType (时间节点重启类型)

=== "中文"

    这种简单的类型决定了效果是否可以多次播放。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    always (重新启动枚举 ( Always )) 
                </td>
                <td>
                    始终重新启动节点
                </td>
            </tr>
            <tr>
                <td>
                    never (重新启动枚举 ( Never )) 
                </td>
                <td>
                    永远不要重启节点
                </td>
            </tr>
            <tr>
                <td>
                    whenNotActive (重新启动枚举 ( When Not Active ))
                </td>
                <td>
                    当节点不活动时重新启动
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodeRestartType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeRestartType (Time Node Restart Type)**

    This simple type determines whether an effect can play more than once.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    always (Restart Enum ( Always )) 
                </td>
                <td>
                    Always restart node
                </td>
            </tr>
            <tr>
                <td>
                    never (Restart Enum ( Never )) 
                </td>
                <td>
                    Never restart node
                </td>
            </tr>
            <tr>
                <td>
                    whenNotActive (Restart Enum ( When Not Active ))
                </td>
                <td>
                    Restart when node is not active
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeRestartType) is located in §A.3. end note]

## 19.7.46 ST_TLTimeNodeSyncType (时间节点同步类型)

=== "中文"

    这个简单类型指定时间节点如何与其组同步。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    canSlip (TimeNode 同步枚举 ( Can Slip )) 
                </td>
                <td>
                    可以滑动
                </td>
            </tr>
            <tr>
                <td>
                    locked (TimeNode 同步枚举 ( Locked )) 
                </td>
                <td>
                    锁定
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodeSyncType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeSyncType (Time Node Sync Type)**

    This simple type specifies how the time node synchronizes to its group.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    canSlip (TimeNode Sync Enum ( Can Slip )) 
                </td>
                <td>
                    Can Slip
                </td>
            </tr>
            <tr>
                <td>
                    locked (TimeNode Sync Enum ( Locked )) 
                </td>
                <td>
                    Locked
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeSyncType) is located in §A.3. end note]

## 19.7.47 ST_TLTimeNodeType (时间节点类型)

=== "中文"

    这个简单类型指定时间节点类型。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    此简单类型仅限于下表中列出的值：
    
    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    afterEffect (节点类型枚举 ( After Effect )) 
                </td>
                <td>
                    后期效果
                </td>
            </tr>
            <tr>
                <td>
                    afterGroup (节点类型枚举 ( After Group )) 
                </td>
                <td>
                    组后
                </td>
            </tr>
            <tr>
                <td>
                    clickEffect (节点类型枚举 ( Click Effect ))  
                </td>
                <td>
                    点击效果
                </td>
            </tr>
            <tr>
                <td>
                    clickPar (节点类型枚举 ( Click Paragraph )) 
                </td>
                <td>
                    单击段落
                </td>
            </tr>
            <tr>
                <td>
                    interactiveSeq (节点类型枚举 ( Interactive Sequence ))
                </td>
                <td>
                    互动序列
                </td>
            </tr>
            <tr>
                <td>
                    mainSeq (节点类型枚举 ( Main Sequence )) 
                </td>
                <td>
                    主序列
                </td>
            </tr>
            <tr>
                <td>
                    tmRoot (节点类型枚举 ( Timing Root )) 
                </td>
                <td>
                    时序根
                </td>
            </tr>
            <tr>
                <td>
                    withEffect (节点类型枚举 ( With Effect )) 
                </td>
                <td>
                    有效果
                </td>
            </tr>
            <tr>
                <td>
                    withGroup (节点类型枚举 ( With Group )) 
                </td>
                <td>
                    与组一起
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTimeNodeType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTimeNodeType (Time Node Type)**

    This simple type specifies time node types.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    afterEffect (Node Type Enum ( After Effect )) 
                </td>
                <td>
                    After Effect
                </td>
            </tr>
            <tr>
                <td>
                    afterGroup (Node Type Enum ( After Group )) 
                </td>
                <td>
                    After Group
                </td>
            </tr>
            <tr>
                <td>
                    clickEffect (Node Type Enum ( Click Effect ))  
                </td>
                <td>
                    Click Effect
                </td>
            </tr>
            <tr>
                <td>
                    clickPar (Node Type Enum ( Click Paragraph )) 
                </td>
                <td>
                    Click Paragraph
                </td>
            </tr>
            <tr>
                <td>
                    interactiveSeq (Node Type Enum ( Interactive Sequence ))
                </td>
                <td>
                    Interactive Sequence
                </td>
            </tr>
            <tr>
                <td>
                    mainSeq (Node Type Enum ( Main Sequence )) 
                </td>
                <td>
                    Main Sequence
                </td>
            </tr>
            <tr>
                <td>
                    tmRoot (Node Type Enum ( Timing Root )) 
                </td>
                <td>
                    Timing Root
                </td>
            </tr>
            <tr>
                <td>
                    withEffect (Node Type Enum ( With Effect )) 
                </td>
                <td>
                    With Effect
                </td>
            </tr>
            <tr>
                <td>
                    withGroup (Node Type Enum ( With Group )) 
                </td>
                <td>
                    With Group
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTimeNodeType) is located in §A.3. end note]

## 19.7.48 ST_TLTriggerEvent (触发事件)

=== "中文"

    这个简单类型指定导致时间条件为真的特定事件。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    begin (触发事件枚举 ( Begin )) 
                </td>
                <td>
                    一开始就触发
                </td>
            </tr>
            <tr>
                <td>
                    end (触发事件枚举 ( End )) 
                </td>
                <td>
                    最后触发
                </td>
            </tr>
            <tr>
                <td>
                    onBegin (触发事件枚举 ( On Begin ))
                </td>
                <td>
                    一开始就触发
                </td>
            </tr>
            <tr>
                <td>
                    onClick (触发事件枚举 ( On Click )) 
                </td>
                <td>
                    单击鼠标触发
                </td>
            </tr>
            <tr>
                <td>
                    onDblClick (触发事件枚举 ( On Double Click ))  
                </td>
                <td>
                    双击鼠标触发
                </td>
            </tr>
            <tr>
                <td>
                    onEnd (触发事件枚举 ( On End )) 
                </td>
                <td>
                    最后触发
                </td>
            </tr>
            <tr>
                <td>
                    onMouseOut (触发事件枚举 ( On Mouse Out )) 
                </td>
                <td>
                    鼠标移出时触发
                </td>
            </tr>
            <tr>
                <td>
                    onMouseOver (触发事件枚举 ( On Mouse Over ))
                </td>
                <td>
                    鼠标悬停时触发
                </td>
            </tr>
            <tr>
                <td>
                    onNext (触发事件枚举 ( On Next )) 
                </td>
                <td>
                    触发下一个节点时
                </td>
            </tr>
            <tr>
                <td>
                    onPrev (触发事件枚举 ( On Previous ))
                </td>
                <td>
                    前一个节点上的触发触发器
                </td>
            </tr>
            <tr>
                <td>
                    onStopAudio (触发事件枚举 ( On Stop Audio ))
                </td>
                <td>
                    停止音频时触发触发
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTriggerEvent) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTriggerEvent (Trigger Event)**

    This simple type specifies a particular event that causes the time condition to be true.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
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
                <td>
                    begin (Trigger Event Enum ( Begin )) 
                </td>
                <td>
                    Fire trigger at the beginning
                </td>
            </tr>
            <tr>
                <td>
                    end (Trigger Event Enum ( End )) 
                </td>
                <td>
                    Fire trigger at the end
                </td>
            </tr>
            <tr>
                <td>
                    onBegin (Trigger Event Enum ( On Begin ))
                </td>
                <td>
                    Fire trigger at the beginning
                </td>
            </tr>
            <tr>
                <td>
                    onClick (Trigger Event Enum ( On Click )) 
                </td>
                <td>
                    Fire trigger on a mouse click
                </td>
            </tr>
            <tr>
                <td>
                    onDblClick (Trigger Event Enum ( On Double Click ))  
                </td>
                <td>
                    Fire trigger on double-mouse click
                </td>
            </tr>
            <tr>
                <td>
                    onEnd (Trigger Event Enum ( On End )) 
                </td>
                <td>
                    Fire trigger at the end
                </td>
            </tr>
            <tr>
                <td>
                    onMouseOut (Trigger Event Enum ( On Mouse Out )) 
                </td>
                <td>
                    Fire trigger on mouse out
                </td>
            </tr>
            <tr>
                <td>
                    onMouseOver (Trigger Event Enum ( On Mouse Over ))
                </td>
                <td>
                    Fire trigger on mouse over
                </td>
            </tr>
            <tr>
                <td>
                    onNext (Trigger Event Enum ( On Next )) 
                </td>
                <td>
                    Fire trigger on next node
                </td>
            </tr>
            <tr>
                <td>
                    onPrev (Trigger Event Enum ( On Previous ))
                </td>
                <td>
                    Fire trigger on previous node
                </td>
            </tr>
            <tr>
                <td>
                    onStopAudio (Trigger Event Enum ( On Stop Audio ))
                </td>
                <td>
                    Fire trigger on stop audio
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTriggerEvent) is located in §A.3. end note]

## 19.7.49 ST_TLTriggerRuntimeNode (触发运行时节点)

=== "中文"

    这个简单类型指定触发时间条件的子时间节点。 引用子 TimeNode 或全部

    子节点。 顺序根据孩子的结束时间而定。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    all (触发器运行时节点枚举 ( All )) 
                </td>
                <td>
                    全部
                </td>
            </tr>
            <tr>
                <td>
                    first (触发器运行时节点枚举 ( First )) 
                </td>
                <td>
                    首先
                </td>
            </tr>
            <tr>
                <td>
                    last (触发器运行时节点枚举 ( Last )) 
                </td>
                <td>
                    最后
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TLTriggerRuntimeNode) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TLTriggerRuntimeNode (Trigger RunTime Node)**

    This simple type specifies the child time node that triggers a time condition. References a child TimeNode or all

    child nodes. Order is based on the child's end time.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    all (Trigger RunTime Node Enum ( All )) 
                </td>
                <td>
                    All
                </td>
            </tr>
            <tr>
                <td>
                    first (Trigger RunTime Node ( First )) 
                </td>
                <td>
                    First
                </td>
            </tr>
            <tr>
                <td>
                    last (Trigger RunTime Node ( Last )) 
                </td>
                <td>
                    Last
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TLTriggerRuntimeNode) is located in §A.3. end note]

## 19.7.50 ST_TransitionCornerDirectionType (过渡角方向类型)

=== "中文"

    这种简单的类型指定幻灯片过渡的对角线方向。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    ld (过渡角方向枚举 ( Left-Down )) 
                </td>
                <td>
                    指定幻灯片过渡方向为左下
                </td>
            </tr>
            <tr>
                <td>
                    lu (过渡角方向枚举 ( Left-Up )) 
                </td>
                <td>
                    指定幻灯片过渡方向为左上
                </td>
            </tr>
            <tr>
                <td>
                    rd (过渡角方向枚举 ( Right-Down )) 
                </td>
                <td>
                    指定幻灯片过渡方向为右下
                </td>
            </tr>
            <tr>
                <td>
                    ru (过渡角方向枚举 ( Right-Up )) 
                </td>
                <td>
                    指定幻灯片过渡方向为右上
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TransitionCornerDirectionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TransitionCornerDirectionType (Transition Corner Direction Type)**

    This simple type specifies diagonal directions for slide transitions.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    ld (Transition Corner Direction Enum ( Left-Down )) 
                </td>
                <td>
                    Specifies the slide transition direction of left-down
                </td>
            </tr>
            <tr>
                <td>
                    lu (Transition Corner Direction Enum ( Left-Up )) 
                </td>
                <td>
                    Specifies the slide transition direction of left-up
                </td>
            </tr>
            <tr>
                <td>
                    rd (Transition Corner Direction Enum ( Right-Down )) 
                </td>
                <td>
                    Specifies the slide transition direction of right-down
                </td>
            </tr>
            <tr>
                <td>
                    ru (Transition Corner Direction Enum ( Right-Up )) 
                </td>
                <td>
                    Specifies the slide transition direction of right-up
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionCornerDirectionType) is located in §A.3. end note]

## 19.7.51 ST_TransitionEightDirectionType (过渡八方向)

=== "中文"

    这个简单的类型指定动画的方向。

    这个简单类型是以下类型的联合：

    - ST_TransitionCornerDirectionType 简单类型 (§19.7.50)。
    - ST_TransitionSideDirectionType 简单类型 (§19.7.53)。

    [Note: 此简单类型的内容模型 (ST_TransitionEightDirectionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TransitionEightDirectionType (Transition Eight Direction)**

    This simple type specifies the direction of an animation.

    This simple type is a union of the following types:

    - The ST_TransitionCornerDirectionType simple type (§19.7.50).
    - The ST_TransitionSideDirectionType simple type (§19.7.53).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionEightDirectionType) is located in §A.3. end note]

## 19.7.52 ST_TransitionInOutDirectionType (过渡输入/输出方向类型)

=== "中文"

    这个简单的类型指定幻灯片过渡是否应该进入或退出。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    in (过渡输入/输出方向枚举 ( In )) 
                </td>
                <td>
                    指定幻灯片过渡应进入
                </td>
            </tr>
            <tr>
                <td>
                    out (过渡输入/输出方向枚举 ( Out ))
                </td>
                <td>
                    指定幻灯片过渡应该消失
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TransitionInOutDirectionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TransitionInOutDirectionType (Transition In/Out Direction Type)**

    This simple type specifies if a slide transition should go in or out.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    in (Transition In/Out Direction Enum ( In )) 
                </td>
                <td>
                    Specifies the slide transition should go in
                </td>
            </tr>
            <tr>
                <td>
                    out (Transition In/Out Direction Enum ( Out ))
                </td>
                <td>
                    Specifies the slide transition should go out
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionInOutDirectionType) is located in §A.3. end note]

## 19.7.53 ST_TransitionSideDirectionType (过渡侧向型)

=== "中文"

    这个简单的类型定义了一组幻灯片过渡方向。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    d (过渡侧方向枚举 ( Down )) 
                </td>
                <td>
                    指定过渡方向为向下
                </td>
            </tr>
            <tr>
                <td>
                    l (过渡侧方向枚举 ( Left )) 
                </td>
                <td>
                    指定过渡方向为向左
                </td>
            </tr>
            <tr>
                <td>
                    r (过渡侧方向枚举 ( Right )) 
                </td>
                <td>
                    指定过渡方向是向右
                </td>
            </tr>
            <tr>
                <td>
                    u (过渡侧方向枚举 ( Up )) 
                </td>
                <td>
                    指定过渡方向为向上
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_TransitionSideDirectionType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_TransitionSideDirectionType (Transition Side Direction Type)**

    This simple type defines a set of slide transition directions.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    d (Transition Side Direction Enum ( Down )) 
                </td>
                <td>
                    Specifies that the transition direction is down
                </td>
            </tr>
            <tr>
                <td>
                    l (Transition Side Direction Enum ( Left )) 
                </td>
                <td>
                    Specifies that the transition direction is left
                </td>
            </tr>
            <tr>
                <td>
                    r (Transition Side Direction ( Right )) 
                </td>
                <td>
                    Specifies that the transition direction is right
                </td>
            </tr>
            <tr>
                <td>
                    u (Transition Side Direction Enum ( Up )) 
                </td>
                <td>
                    Specifies that the transition direction is up
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionSideDirectionType) is located in §A.3. end note]

## 19.7.54 ST_TransitionSpeed (过渡速度)

=== "中文"

    这个简单的类型定义了从当前幻灯片过渡到下一张幻灯片所允许的过渡速度。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    fast (Fast) 
                </td>
                <td>
                    快速幻灯片切换。
                </td>
            </tr>
            <tr>
                <td>
                    med (Medium) 
                </td>
                <td>
                    中等幻灯片过渡。
                </td>
            </tr>
            <tr>
                <td>
                    slow (low) 
                </td>
                <td>
                    缓慢的幻灯片过渡。
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionSpeed) is located in §A.3. end note]

=== "英文"

    **ST_TransitionSpeed (Transition Speed)**

    This simple type defines the allowed transition speeds for transitioning from the current slide to the next.

    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    fast (Fast) 
                </td>
                <td>
                    Fast slide transition.
                </td>
            </tr>
            <tr>
                <td>
                    med (Medium) 
                </td>
                <td>
                    Medium slide transition.
                </td>
            </tr>
            <tr>
                <td>
                    slow (low) 
                </td>
                <td>
                    Slow slide transition.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TransitionSpeed) is located in §A.3. end note]

## 19.7.55 ST_ViewType (视图类型列表)

=== "中文"

    这个简单的类型定义了应用程序在呈现PresentationML 文档时可用的视图类型。 这些视图类型如下：讲义视图、普通幻灯片视图、笔记母版视图、笔记视图、大纲视图、幻灯片母版视图、幻灯片排序器视图和幻灯片缩略图视图。 [Note：虽然本标准适用于文件格式，但偶尔也会给出有关处理该文件格式之外的内容的意图的指导，例如将文档呈现到屏幕或打印机。 end note]
    
    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。

    此简单类型仅限于下表中列出的值：

    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    handoutView (讲义主视图)
                </td>
                <td>
                    指定应使用某种模板来呈现给定的PresentationML 文档，该模板旨在促进打印讲义的设计和布局的更改。
                </td>
            </tr>
            <tr>
                <td>
                    notesMasterView (笔记主视图)
                </td>
                <td>
                    指定应使用某种模板来呈现给定的PresentationML 文档，该模板旨在促进笔记幻灯片的设计和布局的更改。
                </td>
            </tr>
            <tr>
                <td>
                    notesView (笔记视图) 
                </td>
                <td>
                    指定应使用某种旨在方便查看或编辑注释的模板来呈现给定的PresentationML 文档。
                </td>
            </tr>
            <tr>
                <td>
                    outlineView (轮廓视图) 
                </td>
                <td>
                    指定应在视图中呈现给定的PresentationML 文档，该视图旨在方便以某种大纲形式查看幻灯片。
                </td>
            </tr>
            <tr>
                <td>
                    sldMasterView (幻灯片母版视图) 
                </td>
                <td>
                    指定应使用某种模板来呈现给定的PresentationML 文档，该模板旨在促进更改母版幻灯片的设计和布局。
                </td>
            </tr>
            <tr>
                <td>
                    sldSorterView (幻灯片排序器视图) 
                </td>
                <td>
                    指定应在旨在促进幻灯片重新排列的视图中呈现给定的PresentationML 文档。
                </td>
            </tr>
            <tr>
                <td>
                    sldThumbnailView (幻灯片缩略图视图) 
                </td>
                <td>
                    指定应在以某种缩略图形式显示幻灯片的视图中呈现给定的PresentationML文档.
                </td>
            </tr>
            <tr>
                <td>
                    sldView (普通幻灯片视图) 
                </td>
                <td>
                    指定应在允许查看或编辑幻灯片的视图中呈现给定的PresentationML文档.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此简单类型的内容模型 (ST_ViewType) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ST_ViewType (List of View Types)**
    
    This simple type defines the kinds of view available to an application when rendering a PresentationML document. Those view kinds are, as follows: handout view, normal slide view, notes master view, notes view, outline view, slide master view, slide sorter view, and slide thumbnail view. [Note: Although this Standard is for a file format, occasionally, guidance is given regarding intent in dealing with things outside that file format, such as the rendering of documents to a screen or printer. end note]
        
    This simple type's contents are a restriction of the W3C XML Schema token datatype.

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
                <td>
                    handoutView (Handout Master View)
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered using some sort of template that is intended to facilitate the changing of the design and layout of printed handouts.
                </td>
            </tr>
            <tr>
                <td>
                    notesMasterView (Notes Master View)
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered using some sort of template that is intended to facilitate the changing of the design and layout of notes slides.
                </td>
            </tr>
            <tr>
                <td>
                    notesView (Notes View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered using some sort of template that is intended to facilitate the viewing or editing of notes.
                </td>
            </tr>
            <tr>
                <td>
                    outlineView (Outline View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered in a view that is intended to facilitate the viewing of slides in some outline form.
                </td>
            </tr>
            <tr>
                <td>
                    sldMasterView (Slide Master View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered using some sort of template that is intended to facilitate the changing of the design and layout of master slides.
                </td>
            </tr>
            <tr>
                <td>
                    sldSorterView (Slide Sorter View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered in a view that is intended to facilitate the rearrangement of slides.
                </td>
            </tr>
            <tr>
                <td>
                    sldThumbnailView (Slide Thumbnail View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered in a view that shows slides in some thumbnail form.
                </td>
            </tr>
            <tr>
                <td>
                    sldView (Normal Slide View) 
                </td>
                <td>
                    Specifies that a given PresentationML document should be rendered in a view that allows slides to be viewed or edited.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ViewType) is located in §A.3. end note]
