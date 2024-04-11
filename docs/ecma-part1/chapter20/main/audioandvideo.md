# 20.1.3 音频和视频

=== "中文"

    DrawingML 框架的音频和视频部分处理可以附加到文档中的对象的这两种类型的所有媒体。 文件中可以表示的音频类型包括 CD 音频、QuickTime 音频和任何其他通用音频。 处理通用音频时，可以选择将其嵌入文件中并链接它。 如果音频文件的大小太大，从而使文档的大小增加了不希望的量，那么链接选项是优选的。 对于视频，有两种可以表示的类型，即 QuickTime 电影或任何其他通用电影。 处理通用视频时，只能选择链接到媒体，因为视频太大而无法嵌入文档中。

=== "英文"

    **Audio and Video**

    The Audio and Video portion of the DrawingML framework deals with all media of these two kinds that can be attached to objects within a document. Types of audio that can be represented within a file are CD audio, QuickTime audio, and any other generic audio. When dealing with generic audio there is the option for embedding it within the file and also linking it. The linking option is preferable if the size of the audio file is too large and thus increases the size of the document by an undesirable amount. For video there are two kinds that can be represented and that is either a QuickTime movie or any other generic movie. When dealing with generic video there is only the option of linking to the media as video is too large to embed within a document.

## 20.1.3.1 audioCd (CD 中的音频)

=== "中文"

    该元素指定 CD 中是否存在音频。 该元素在对象的非视觉属性中指定。 音频应附加到对象，因为这是它在文档中的表示方式。 然而，声音的实际播放是在计时元素下指定的计时节点列表内完成的。

    !!! info "Example"

        考虑以下图片对象，其中附有 CD 中的音频。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:audioCd>
                        <a:st track="1"/>
                        <a:end track="3" time="65"/>
                    </a:audioCd>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        在上面的示例中，我们看到该图片附加了一个 audioCD 元素。 该图片就像普通图片或形状一样放置在文档中。 该图片的 id（在本例中为 7）用于引用定时节点列表中的该 audioCD 元素。 在此示例中，我们看到该 CD 的音频在第一首曲目的 0 秒标记处开始播放，并在第三首曲目的 1 分 5 秒标记处结束。

    [Note: 该元素内容模型 (CT_AudioCD) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **audioCd (Audio from CD)**

    This element specifies the existence of Audio from a CD. This element is specified within the non-visual properties of an object. The audio shall be attached to an object as this is how it is represented within the document. The actual playing of the sound however is done within the timing node list that is specified under the timing element.

    !!! info "Example"

        Consider the following picture object that has an audio from a CD attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:audioCd>
                        <a:st track="1"/>
                        <a:end track="3" time="65"/>
                    </a:audioCd>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        In the above example, we see that there is a single audioCD element attached to this picture. This picture is placed within the document just as a normal picture or shape would be. The id of this picture, namely 7 in this case, is used to refer to this audioCD element from within the timing node list. For this example we see that the audio for this CD starts playing at the 0 second mark on the first track and ends on the 1 minute 5 second mark of the third track. 

    [Note: The W3C XML Schema definition of this element’s content model (CT_AudioCD) is located in §A.4.1. end note]

## 20.1.3.2 audioFile (文件中的音频)

=== "中文"

    该元素指定音频文件的存在。 该元素在对象的非视觉属性中指定。 音频应附加到对象，因为这是它在文档中的表示方式。 然而，音频的实际播放是在计时元素下指定的计时节点列表内完成的。

    !!! info "Example"

        考虑以下附加有音频文件的图片对象。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:audioFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        在上面的示例中，我们看到该图片附加了一个 audioFile 元素。 该图片就像普通图片或形状一样放置在文档中。 该图片的 id（在本例中为 7）用于引用定时节点列表中的该 audioFile 元素。 链接关系 ID 用于检索实际音频文件以进行播放。

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
                    contentType (链接音频文件的内容类型/Content Type of Linked Audio File)
                </td>
                <td>
                    指定此元素引用的外部文件的内容类型。 内容类型定义媒体类型、子类型和可选参数集，如第 2 部分中所定义。如果呈现应用程序无法处理指定内容类型的外部内容，则可以忽略指定内容. [Note: [§15.2.2] 中提供了建议的音频类型列表。 end note]</br></br>
                    如果省略此属性，应用程序应尝试通过读取关系目标的内容来确定内容类型.</br></br>
                    想要互操作性的生产者应该使用以下标准格式:</br>
                    • audio/mpeg ISO/IEC 11172-3</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    link (关联关系 ID/Linked Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定链接对象的标识信息。 该属性用于指定不驻留在该文件中的对象的位置.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AudioFile) 的 W3C XML 架构定义位于 §A.4.1. 中  end note]

=== "英文"

    **audioFile (Audio from File)**

    This element specifies the existence of an audio file. This element is specified within the non-visual properties of an object. The audio shall be attached to an object as this is how it is represented within the document. The actual playing of the audio however is done within the timing node list that is specified under the timing element.

    !!! info "Example"

        Consider the following picture object that has an audio file attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:audioFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        In the above example, we see that there is a single audioFile element attached to this picture. This picture is placed within the document just as a normal picture or shape would be. The id of this picture, namely 7 in this case, is used to refer to this audioFile element from within the timing node list. The Linked relationship id is used to retrieve the actual audio file for playback purposes.

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
                    contentType (Content Type of Linked Audio File)
                </td>
                <td>
                    Specifies the content type for the external file that is referenced by this element. Content types define a media type, a subtype, and an optional set of parameters, as defined in Part 2. If a rendering application cannot process external content of the content type specified, then the specified content can be ignored. [Note: A list of suggested audio types is provided in §15.2.2. end note]</br></br>
                    If this attribute is omitted, application should attempt to determine the content type by reading the contents of the relationship’s target.</br></br>
                    A producer that wants interoperability should use the following standard format:</br>
                    • audio/mpeg ISO/IEC 11172-3</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    link (Linked Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the identification information for a linked object. This attribute is used to specify the location of an object that does not reside within this file.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AudioFile) is located in §A.4.1. end note]

## 20.1.3.3 end (音频结束时间)

=== "中文"

    **end (Audio End Time)**

    该元素指定 CD 音频声音元素的结束点。 该元素包含声音应停止播放的时间和曲目。 该元素与音频开始时间元素结合使用来指定整个audioCD声音元素的时间跨度。

    !!! info "Example"

        考虑以下 DrawingML。

        ```xml
        <a:audioCd>
            <a:st track="1" time="2"/>
            <a:end track="3" time="65"/>
        </a:audioCd>
        ```

        在上面的示例中，所示的audioCD声音元素指定了从第一个轨道的2秒到第三个轨道的1分5秒的音频部分。

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
                    time (时间)
                </td>
                <td>
                    指定 CD 音频应停止的时间（以秒为单位）。 如果省略该属性，则假定值为 0.</br></br>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    track (轨道)
                </td>
                <td>
                    指定此音频在 CD 的哪个轨道上停止播放。 该属性为必填项，不能省略.</br></br>
                    此属性的可能值由 W3C XML 架构 unsignedByte 数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AudioCDTime) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **end (Audio End Time)**

    This element specifies the end point for a CD Audio sound element. Encompassed within this element are the time and track at which the sound should halt its playback. This element is used in conjunction with an Audio Start Time element to specify the time span for an entire audioCD sound element.

    !!! info "Example"

        Consider the following DrawingML.

        ```xml
        <a:audioCd>
            <a:st track="1" time="2"/>
            <a:end track="3" time="65"/>
        </a:audioCd>
        ```

        In the above example, the audioCD sound element shown specifies for a portion of audio spanning from 2 seconds into the first track to 1 minute, 5 seconds into the third track.

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
                    time (Time)
                </td>
                <td>
                    Specifies the time in seconds that the CD Audio should be stopped at. If this attribute is omitted, then a value of 0 is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
            <tr>
                <td>
                    track (Track)
                </td>
                <td>
                    Specifies which track of the CD this Audio stops playing at. This attribute is required and cannot be omitted.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedByte datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AudioCDTime) is located in §A.4.1. end note]

## 20.1.3.4 quickTimeFile (来自文件的 QuickTime)

=== "中文"

    此元素指定 QuickTime 文件是否存在，如 2007-09-04 版本的 QuickTime 文件格式规范中所定义: http://developer.apple.com/documentation/QuickTime/QTFF/qtff.pdf. [Note: 有关 QuickTime 格式的更多信息: http://developer.apple.com/reference/QuickTime/. end note]. 该元素在对象的非视觉属性中指定。 QuickTime 文件应附加到对象，因为这是它在文档中的表示方式。 然而，QuickTime 的实际播放是在计时元素下指定的计时节点列表内完成的。

    !!! info "Example"

        考虑以下附加有 QuickTime 文件的图片对象。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:quickTimeFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        在上面的示例中，我们看到该图片附加了一个 QuickTimeFile 元素。 该图片就像普通图片或形状一样放置在文档中。 该图片的 id（在本例中为 7）用于引用计时节点列表中的该 QuickTimeFile 元素。 链接关系 ID 用于检索实际视频文件以进行播放. 

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
                    link (关联关系 ID/Linked Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定链接对象的标识信息。 该属性用于指定不驻留在该文件中的对象的位置.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_QuickTimeFile) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **quickTimeFile (QuickTime from File)**

    This element specifies the existence of a QuickTime file, as defined in the 2007-09-04 version of the QuickTime File Format Specification: http://developer.apple.com/documentation/QuickTime/QTFF/qtff.pdf. [Note: For more information on the QuickTime format: http://developer.apple.com/reference/QuickTime/. end note]. This element is specified within the non-visual properties of an object. The QuickTime file shall be attached to an object as this is how it is represented within the document. The actual playing of the QuickTime however is done within the timing node list that is specified under the timing element.

    !!! info "Example"

        Consider the following picture object that has a QuickTime file attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:quickTimeFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        In the above example, we see that there is a single quickTimeFile element attached to this picture. This picture is placed within the document just as a normal picture or shape would be. The id of this picture, namely 7 in this case, is used to refer to this quickTimeFile element from within the timing node list. The Linked relationship id is used to retrieve the actual video file for playback purposes. 

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
                    link (Linked Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the identification information for a linked object. This attribute is used to specify the location of an object that does not reside within this file.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_QuickTimeFile) is located in §A.4.1. end note]

## 20.1.3.5 st (音频开始时间)

=== "中文"

    该元素指定 CD 音频声音元素的起点。 该元素包含声音应开始播放的时间和曲目。 该元素与音频结束时间元素结合使用来指定整个audioCD声音元素的时间跨度。

    !!! info "Example"

        考虑以下 DrawingML。

        ```xml
        <a:audioCd>
            <a:st track="1" time="2"/>
            <a:end track="3" time="65"/>
        </a:audioCd>
        ```

        在上面的示例中，所示的 audioCD 声音元素指定了从第一个轨道的2秒到第三个轨道的1分5秒的音频部分。

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
                    time (时间)
                </td>
                <td>
                    指定 CD 音频应启动的时间（以秒为单位）。 如果省略该属性，则假定值为 0.</br></br>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    track (轨道)
                </td>
                <td>
                    指定此音频开始在 CD 的哪个轨道上播放。 该属性为必填项，不能省略.</br></br>
                    此属性的可能值由 W3C XML 架构 unsignedByte 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AudioCDTime) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **st (Audio Start Time)**

    This element specifies the start point for a CD Audio sound element. Encompassed within this element are the time and track at which the sound should begin its playback. This element is used in conjunction with an Audio End Time element to specify the time span for an entire audioCD sound element.

    !!! info "Example"

        Consider the following DrawingML.

        ```xml
        <a:audioCd>
            <a:st track="1" time="2"/>
            <a:end track="3" time="65"/>
        </a:audioCd>
        ```

        In the above example, the audioCD sound element shown specifies for a portion of audio spanning from 2 seconds into the first track to 1 minute, 5 seconds into the third track.

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
                    time (Time)
                </td>
                <td>
                    Specifies the time in seconds that the CD Audio should be started at. If this attribute is omitted, then a value of 0 is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
            <tr>
                <td>
                    track (Track)
                </td>
                <td>
                    Specifies which track of the CD this Audio begins playing on. This attribute is required and cannot be omitted.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedByte datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AudioCDTime) is located in §A.4.1. end note]

## 20.1.3.6 videoFile (文件中的视频)

=== "中文"

    该元素指定视频文件的存在。 该元素在对象的非视觉属性中指定。 视频应附加到对象上，因为这是它在文档中的表示方式。 然而，视频的实际播放是在定时元素下指定的定时节点列表内完成的。

    !!! info "Example"

        考虑下面附加了视频的图片对象。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:videoFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        在上面的示例中，我们看到该图片附加了一个 videoFile 元素。 该图片就像普通图片或形状一样放置在文档中。 该图片的 id（在本例中为 7）用于引用定时节点列表中的该 videoFile 元素。 链接关系 ID 用于检索实际视频文件以进行播放。

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
                    contentType (链接视频文件的内容类型)
                </td>
                <td>
                    指定此元素引用的外部文件的内容类型。 内容类型定义媒体类型、子类型和可选参数集，如第 2 部分中所定义。如果呈现应用程序无法处理指定内容类型的外部内容，则可以忽略指定内容. [Note: 第 15.2.17 节中提供了建议的视频类型列表。 end note]</br></br>
                    如果省略此属性，应用程序应尝试通过读取关系目标的内容来确定内容类型.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    link (关联关系 ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定链接视频文件的标识信息。 该属性用于指定不驻留在该文件中的对象的位置.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_VideoFile) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **videoFile (Video from File)**

    This element specifies the existence of a video file. This element is specified within the non-visual properties of an object. The video shall be attached to an object as this is how it is represented within the document. The actual playing of the video however is done within the timing node list that is specified under the timing element.

    !!! info "Example"

        Consider the following picture object that has a video attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:videoFile r:link="rId1"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```

        In the above example, we see that there is a single videoFile element attached to this picture. This picture is placed within the document just as a normal picture or shape would be. The id of this picture, namely 7 in this case, is used to refer to this videoFile element from within the timing node list. The Linked relationship id is used to retrieve the actual video file for playback purposes.

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
                    contentType (Content Type of Linked Video File)
                </td>
                <td>
                    Specifies the content type for the external file that is referenced by this element. Content types define a media type, a subtype, and an optional set of parameters, as defined in Part 2. If a rendering application cannot process external content of the content type specified, then the specified content can be ignored. [Note: A list of suggested video types is provided in §15.2.17. end note]</br></br>
                    If this attribute is omitted, application should attempt to determine the content type by reading the contents of the relationship’s target.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    link (Linked Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the identification information for a linked video file. This attribute is used to specify the location of an object that does not reside within this file.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_VideoFile) is located in §A.4.1. end note]

## 20.1.3.7 wavAudioFile (WAV 文件中的音频)

=== "中文"

    该元素指定音频 WAV 文件是否存在。 该元素在对象的非视觉属性中指定。 音频应附加到对象，因为这是它在文档中的表示方式。 然而，音频的实际播放是在计时元素下指定的计时节点列表内完成的。

    !!! info "Example"

        考虑以下附加有音频 WAV 文件的图片对象。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:wavAudioFile r:embed="rId2"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```
        
        在上面的示例中，我们看到该图片附加了一个 wavAudioFile 元素。 该图片就像普通图片或形状一样放置在文档中。 该图片的 id（在本例中为 7）用于引用定时节点列表中的该 wavAudioFile 元素。 嵌入关系 ID 用于检索实际音频文件以进行播放。

        [Note: 该元素通常用于在文档中嵌入音频文件。 要链接到通用音频文件，应使用 audioFile 元素. end note]

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
                    embed (嵌入音频文件关系 ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定嵌入音频文件的标识信息。 该属性用于指定本地驻留在文件内的对象的位置. [Note: §15.2.2 节中提供了建议的音频类型列表。 end note]</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型 (§22.8.2.1) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    name (声音名称)
                </td>
                <td>
                    指定相应声音的原始名称或给定的短名称。 如果用户需要在 UI 中的其他声音中识别该声音，则可以通过为附加声音提供人类可读的名称来区分该声音与其他声音.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_EmbeddedWAVAudioFile) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **wavAudioFile (Audio from WAV File)**

    This element specifies the existence of an audio WAV file. This element is specified within the non-visual properties of an object. The audio shall be attached to an object as this is how it is represented within the document. The actual playing of the audio however is done within the timing node list that is specified under the timing element.

    !!! info "Example"

        Consider the following picture object that has an audio WAV file attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="7" name="Rectangle 6">
                    <a:hlinkClick r:id="" action="ppaction://media"/>
                </p:cNvPr>
                <p:cNvPicPr>
                    <a:picLocks noRot="1"/>
                </p:cNvPicPr>
                <p:nvPr>
                    <a:wavAudioFile r:embed="rId2"/>
                </p:nvPr>
            </p:nvPicPr>
            …
        </p:pic>
        ```
        
        In the above example, we see that there is a single wavAudioFile element attached to this picture. This picture is placed within the document just as a normal picture or shape would be. The id of this picture, namely 7 in this case, is used to refer to this wavAudioFile element from within the timing node list. The Embedded relationship id is used to retrieve the actual audio file for playback purposes. 

        [Note: This element is generally used for the purposes of embedding audio files within the document. For linking to generic audio files the audioFile element should be used. end note]

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
                    embed (Embedded Audio File Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the identification information for an embedded audio file. This attribute is used to specify the location of an object that resides locally within the file. [Note: A list of suggested audio types is provided in §15.2.2. end note]</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
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
