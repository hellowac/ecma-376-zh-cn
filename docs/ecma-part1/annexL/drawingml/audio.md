# L.4.2 音频和视频

**Audio and Video**

## L.4.2.1 介绍

=== "中文"

    DrawingML 包含对基本音频和视频功能的支持。

=== "英文"

    **Introduction**

    DrawingML contains support for basic audio and video capabilities.

## L.4.2.2 功能概述

=== "中文"

    演示文稿作者可以指定在幻灯片放映中显示幻灯片时可以播放音频和视频。 将此类媒体插入演示文稿时，演示文稿作者可以指定该媒体自动播放（即，根据幻灯片的动画时间线）或响应鼠标单击。 无论哪种情况，媒体仅在指定的时间内播放，或者直到幻灯片发生变化（以较短者为准）。

    音频内容的来源包括基于 CD 的文件以及更传统的基于 Discord 服务器的文件。

    当插入 CD 上存储的音频内容时，作者可以指定开始和结束轨道，以及每个轨道的索引。 该信息标识在幻灯片放映期间要为指定幻灯片播放的 CD 内容。
    
    如果音频或视频内容存储在硬盘或服务器上，作者只能指定文件本身； 它会完整播放，或者直到幻灯片发生变化。

=== "英文"

    **Functional Overview**

    Presentation authors can specify that both audio and video can play while a slide is shown in slide show. When such media is inserted into a presentation, a presentation author can specify that the media is to play automatically (that is, in accordance with the slide’s animation timeline) or in response to a mouseclick. In either case, media only plays for the duration of time specified, or until the slide changes, whichever is shorter.

    Sources for audio content include CD-based files as well as the more traditional disc- or server-based files.

    When inserting audio content stored on a CD, the author can specify a start and end track, as well as an index into each track. This information identifies the content from the CD to be played for the specified slide during a slide show.
    
    In cases where the audio or video content is stored on a hard drive or server, the author can only specify the file itself; it is played in its entirety, or until the slide changes.

## L.4.2.3 DrawingML 语法

=== "中文"

    在所有三种情况下，媒体对象本身都是使用图片形状存储在幻灯片上的。图片形状使用blipFill来显示幻灯片表面上的媒体对象。在两种音频情况下，使用的图片是图标图像，而在视频情况下，使用的图片是视频文件的海报帧。
    
    为了表达这些信息，使用标准的blipFill元素来引用图像文件；因为这是指包内的文件，所以使用了关系ID:

    ```xml
    <p:pic>
        <p:nvPicPr> …</p:nvPicPr>
        <p:blipFill>
            <a:blip r:embed="rId4" r:link="" />
            <a:stretch>
                <a:fillRect />
            </a:stretch>
        </p:blipFill>
        <p:spPr> … </p:spPr>
    </p:pic>
    ```

    由于媒体对象与幻灯片的时间轴相关——无论是自动播放还是鼠标点击——它们必须以超链接的形式存储互动信息。

    为了表达这个信息，一个超链接被添加到非可视形状属性中；因为它是一个超链接，它也使用了一个关系ID：

    ```xml
    <p:pic>
        <p:nvPicPr>
            <p:cNvPr id="15" name="Rectangle 15" descr="">
                <a:hlinkClick r:id="rId3" tgtFrame="" tooltip="" />
            </p:cNvPr>
            <p:cNvPicPr />
            <p:nvPr> … </p:nvPr>
        </p:nvPicPr>
        <p:blipFill> … </p:blipFill>
        <p:spPr> … </p:spPr>
    </p:pic>
    ```

    每种媒体类型所需的最后一条信息是源位。 在这两种基于文件的媒体情况下，DrawingML 都需要提供一种机制来指定媒体的位置和文件名； 这与仅需要轨道信息的基于 CD 的音频形成鲜明对比。 无论所需的源信息类型如何，所有这些都存储在应用程序定义的非可视属性中。 下面的三个 XML 块分别代表了三种媒体案例，对此进行了说明：

    **CD-Audio**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
        <p:nvPr>
            <a:audioCd>
                <a:st track="2" time="50" />
                <a:end track="3" time="22" />
            </a:audioCd>
        </p:nvPr>
        …
    </p:pic>
    ```

    **File-Audio**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
            <p:nvPr>
                <a:audioFile r:embed="" r:link="rId1" />
            </p:nvPr>
        </p:nvPicPr>
        …
    </p:pic>
    ```

    **File-Video**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
            <p:nvPr>
                <a:videoFile r:embed="" r:link="rId1" />
            </p:nvPr>
        </p:nvPicPr>
        …
    </p:pic>
    ```

    在 CD 音频情况下，无法选择包含源的特定 CD 驱动器。 这是一个功能限制。

    虽然默认情况是链接媒体，但基于文件的媒体也可以将源位作为单独的部分包含在包中。 在这种情况下，关系不是指向外部文件，而是指向包内的部件。

=== "英文"

    **DrawingML Syntax**

    In all three cases, the media objects themselves are stored on the slides using a picture shape. The picture shape uses a blipFill to show the media object on the slide’s surface. In both audio cases, the picture used is the icon image, whereas in the video case, the picture used is the poster frame for the video file.

    To express this information, the standard blipFill element is used to refer to the image file; and because this refers to a file within the package, a relationship ID is used:

    ```xml
    <p:pic>
        <p:nvPicPr> …</p:nvPicPr>
        <p:blipFill>
            <a:blip r:embed="rId4" r:link="" />
            <a:stretch>
                <a:fillRect />
            </a:stretch>
        </p:blipFill>
        <p:spPr> … </p:spPr>
    </p:pic>
    ```

    As the media objects are related to the slide’s timeline—in both the automatic and mouse-click cases—they must have interactivity information stored in the form of a hyperlink.

    To express this information, a hyperlink is added to the non-visual shape properties; and because it is a hyperlink, it, too, uses a relationship ID:

    ```xml
    <p:pic>
        <p:nvPicPr>
            <p:cNvPr id="15" name="Rectangle 15" descr="">
                <a:hlinkClick r:id="rId3" tgtFrame="" tooltip="" />
            </p:cNvPr>
            <p:cNvPicPr />
            <p:nvPr> … </p:nvPr>
        </p:nvPicPr>
        <p:blipFill> … </p:blipFill>
        <p:spPr> … </p:spPr>
    </p:pic>
    ```

    The final piece of information required for each media type is the source bits. In both file-based media cases, DrawingML needs to provide a mechanism to specify the location and file name for the media; this is in contrast to the CD-based audio where only track information is required. Regardless of the type of source information required, all of this is stored in application-defined non-visual properties. This is illustrated in the following three XML islands representing each of the three media cases:

    **CD-Audio**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
        <p:nvPr>
            <a:audioCd>
                <a:st track="2" time="50" />
                <a:end track="3" time="22" />
            </a:audioCd>
        </p:nvPr>
        …
    </p:pic>
    ```

    **File-Audio**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
            <p:nvPr>
                <a:audioFile r:embed="" r:link="rId1" />
            </p:nvPr>
        </p:nvPicPr>
        …
    </p:pic>
    ```

    **File-Video**:   

    ```xml
    <p:pic>
        <p:nvPicPr> … <p:cNvPicPr />
            <p:nvPr>
                <a:videoFile r:embed="" r:link="rId1" />
            </p:nvPr>
        </p:nvPicPr>
        …
    </p:pic>
    ```

    In the CD-Audio case, there is no capability to choose the particular CD drive that contains the source. This is a functional limitation.

    While the default case is that media is linked, file-based media can also have the source bits included in the package as a separate part. In this case, the relationships point not to an external file but, rather, to a part inside the package.
