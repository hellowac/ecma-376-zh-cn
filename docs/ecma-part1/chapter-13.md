# 13. PresentationML

=== "中文"

    **PresentationML**

    本节包含特定于PresentationML 的关系项和部件的规范。 [§15.2] 中指定了PresentationML 文档中可能出现但不是 PresentationML 特定的部件。 除非明确说明，否则本条款中对关系项、内容类型项和部件的所有引用均指的是 PresentationML ZIP 项。

=== "英文"

    This clause contains specifications for relationship items and parts that are specific to PresentationML. Parts than can occur in a PresentationML document, but are not PresentationML-specific, are specified in [§15.2]. Unless stated explicitly, all references to relationship items, content-type items, and parts in this clause refer to PresentationML ZIP items.

## 13.1 PresentationML 特定术语词汇表

=== "中文"

    在PresentationML文档的上下文中使用以下术语：
    
    **handout** — 一组打印的幻灯片，可以分发给观众以供将来参考。
    
    **note** — 供演示者或观众使用的幻灯片注释、提醒或文本。
    
    **presentation** — 供观众观看的幻灯片集合。
    
    **slide** — 包含一段或多段文本和/或图像的框架。
    
    **slide layout** — 幻灯片上元素的组织。

=== "英文"

    **Glossary of PresentationML-Specific Terms**

    The following terms are used in the context of a PresentationML document:
    
    **handout** — A printed set of slides that can be handed out to an audience for future reference.
    **note** — A slide annotation, reminder, or piece of text intended for the presenter or the audience.
    **presentation** — A collection of slides intended to be viewed by an audience.
    **slide** — A frame containing one or more pieces of text and/or images.
    **slide layout** — The organization of elements on a slide.

## 13.2 包结构

=== "中文"

    一个PresentationML包应该包含一个包关系项和一个内容类型项。 包关系项应与以下类型的目标具有隐式关系：
    
    * 一份演示文稿部件 ([§13.3.6]).
    
    包关系项允许与以下类型的目标具有隐式关系：
    
    * 数字签名起源 ([§15.2.7])
    * 文件属性部件 ([§15.2.12])（应用程序定义的文件属性、核心文件属性和自定义文件属性）（视情况而定）。
    * 缩略图 ([§15.2.16]).

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}
    
    各部件之间必需的和可选的关系在[§13.3] 及其从属条款中定义。

    !!! note info "样例"
    
        以下包代表 ECMA-376 定义的最小一致的PresentationML包：
        
        首先，必须定义关系部件和主表示部件（唯一必需的部件）的内容类型（物理位置位于包中的 `/[Content_Types].xml`）：

        ```xml
        <Types xmlns="…">
            <Default Extension="rels"
                ContentType="application/vnd.openxmlformats-
                    package.relationships+xml"/>
            <Override PartName="/presentation.xml"
                ContentType="application/vnd.openxmlformats-
                    officedocument.presentationml.presentation.main+xml"/>
        </Types>
        ```

        接下来，必须定义单个必需的关系（与主表示部件的包级关系）（物理上位于包中的 `/_rels/.rels` ）：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" 
                Type="http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument"
                Target="presentation.xml"/>
        </Relationships>
        ```

        最后，必须定义主演示部件的最少内容（物理位置位于包中的 `/presentation.xml`）：

        ```xml
        <p:presentation xmlns:p="…">
            <p:notesSz cx="913607" cy="913607"/>
        </p:presentation>
        ```

    !!! note info "样例"

        考虑一个包含两张幻灯片的简单的 PresentationML 文档，它们都使用图像作为模板。 下面是一个分层文件夹结构的示例，该结构可能用于该文档包中的 ZIP 项目。 如图所示，许多部件都有自己的关系项：

        ```txt
        /_rels/.rels                                        包关系项
        /[Content_Types].xml                                内容类型项目
        /docProps/app.xml                                   应用程序定义的文件属性部件
        /docProps/core.xml                                  核心文件属性部件
        /docProps/custom.xml                                自定义文件属性部件
        /docProps/thumbnail.wmf                             包缩略图
        /ppt/presentation.xml                               演示文稿部件
        /ppt/_rels/presentation.xml.rels                    部件关系项
        /ppt/presProps.xml                                  演示属性部件
        /ppt/tableStyles.xml                                表格样式部件
        /ppt/viewProps.xml                                  查看属性部件
        /ppt/handoutMasters/handoutMaster1.xml              讲义母版部件
        /ppt/handoutMasters/_rels/handoutMaster1.xml.rels   部件关系项
        /ppt/media/image1.jpeg                              幻灯片模板图像
        /ppt/notesMasters/notesMaster1.xml                  笔记母版部件
        /ppt/notesMasters/_rels/notesMaster1.xml.rels       部件关系项
        /ppt/notesSlides/notesSlide1.xml                    笔记幻灯片部件
        /ppt/notesSlides/notesSlide2.xml
        /ppt/notesSlides/_rels/notesSlide1.xml.rels         部件关系项
        /ppt/notesSlides/_rels/notesSlide2.xml.rels
        /ppt/slideLayouts/slideLayout1.xml                  幻灯片布局第 1–6 部件
        /ppt/slideLayouts/slideLayout2.xml
        /ppt/slideLayouts/slideLayout3.xml
        /ppt/slideLayouts/slideLayout4.xml
        /ppt/slideLayouts/slideLayout5.xml
        /ppt/slideLayouts/slideLayout6.xml
        /ppt/slideLayouts/_rels/slideLayout1.xml.rels       部件关系项
        /ppt/slideLayouts/_rels/slideLayout2.xml.rels
        /ppt/slideLayouts/_rels/slideLayout3.xml.rels
        /ppt/slideLayouts/_rels/slideLayout4.xml.rels
        /ppt/slideLayouts/_rels/slideLayout5.xml.rels
        /ppt/slideLayouts/_rels/slideLayout6.xml.rels
        /ppt/slideMasters/slideMaster1.xml                  幻灯片母版部件
        /ppt/slideMasters/_rels/slideMaster1.xml.rels       部件关系项
        /ppt/slides/slide1.xml                              幻灯片部件
        /ppt/slides/slide2.xml
        /ppt/slides/_rels/slide1.xml.rels                   部件关系项
        /ppt/slides/_rels/slide2.xml.rels
        /ppt/theme/theme1.xml                               主题部件
        /ppt/theme/theme2.xml
        /ppt/theme/theme3.xml
        /ppt/theme/themeOverride1.xml                       主题覆盖部件
        /ppt/theme/themeOverride2.xml
        /ppt/theme/themeOverride3.xml
        /ppt/theme/themeOverride4.xml
        /ppt/theme/themeOverride5.xml
        /ppt/theme/themeOverride6.xml
        /ppt/theme/themeOverride7.xml
        /ppt/theme/themeOverride8.xml
        /ppt/theme/themeOverride9.xml
        /ppt/theme/themeOverride10.xml
        ```

        包关系项包含以下内容：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/officeDocument" Target="ppt/presentation.xml"/>
            <Relationship Id="rId3"
                Type="http://…/core-properties" Target="docProps/core.xml"/>
            <Relationship Id="rId2"
                Type="http://…/thumbnail" Target="docProps/thumbnail.wmf"/>
            <Relationship Id="rId4"
                Type="http://…/extended-properties" Target="docProps/app.xml"/>
        </Relationships>
        ```

=== "英文"

    **Package Structure**

    A PresentationML package shall contain a package-relationship item and a content-type item. The packagerelationship item shall have implicit relationships with targets of the following type:
    
    * One Presentation part ([§13.3.6]).
    
    The package-relationship item is permitted to have implicit relationships with targets of the following type:
    
    * Digital Signature Origin ([§15.2.7])
    * File Property parts ([§15.2.12]) (Application-Defined File Properties, Core File Properties, and Custom File Properties), as appropriate.
    * Thumbnail ([§15.2.16]).
    
    The required and optional relationships between parts are defined in [§13.3] and its subordinate clauses.

    !!! note info "样例"
    
        The following package represents the minimal conformant PresentationML package as defined by ECMA-376:
        
        First, the content type for relationship parts and the Main Presentation part (the only required part) must be defined (physically located at /[Content_Types].xml in the package):

        ```xml
        <Types xmlns="…">
            <Default Extension="rels"
                ContentType="application/vnd.openxmlformats-
                    package.relationships+xml"/>
            <Override PartName="/presentation.xml"
                ContentType="application/vnd.openxmlformats-
                    officedocument.presentationml.presentation.main+xml"/>
        </Types>
        ```

        Next, the single required relationship (the package-level relationship to the Main Presentation part) must be defined (physically located at /_rels/.rels in the package):

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" 
                Type="http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument"
                Target="presentation.xml"/>
        </Relationships>
        ```

        Finally, the minimum content for the Main Presentation part must be defined (physically located at /presentation.xml in the package):

        ```xml
        <p:presentation xmlns:p="…">
            <p:notesSz cx="913607" cy="913607"/>
        </p:presentation>
        ```

    !!! note info "样例"

        Consider a simple PresentationML document containing two slides, which both use an image as a template. Here’s an example of the hierarchical folder structure that might be used for the ZIP items in the package for that document. As shown, a number of parts have their own relationship items:

        ```txt
        /_rels/.rels                                        Package-relationship item
        /[Content_Types].xml                                Content-type item
        /docProps/app.xml                                   Application-Defined File Properties part
        /docProps/core.xml                                  Core File Properties part
        /docProps/custom.xml                                Custom File Properties part
        /docProps/thumbnail.wmf                             Package thumbnail image
        /ppt/presentation.xml                               Presentation part
        /ppt/_rels/presentation.xml.rels                    Part-relationship item
        /ppt/presProps.xml                                  Presentation Properties part
        /ppt/tableStyles.xml                                Table Styles part
        /ppt/viewProps.xml                                  View Properties part
        /ppt/handoutMasters/handoutMaster1.xml              Handout Master part
        /ppt/handoutMasters/_rels/handoutMaster1.xml.rels   Part-relationship item
        /ppt/media/image1.jpeg                              Slide template image
        /ppt/notesMasters/notesMaster1.xml                  Notes Master part
        /ppt/notesMasters/_rels/notesMaster1.xml.rels       Part-relationship item
        /ppt/notesSlides/notesSlide1.xml                    Notes Slide parts
        /ppt/notesSlides/notesSlide2.xml
        /ppt/notesSlides/_rels/notesSlide1.xml.rels         Part-relationship items
        /ppt/notesSlides/_rels/notesSlide2.xml.rels
        /ppt/slideLayouts/slideLayout1.xml                  Slide Layout parts 1–6
        /ppt/slideLayouts/slideLayout2.xml
        /ppt/slideLayouts/slideLayout3.xml
        /ppt/slideLayouts/slideLayout4.xml
        /ppt/slideLayouts/slideLayout5.xml
        /ppt/slideLayouts/slideLayout6.xml
        /ppt/slideLayouts/_rels/slideLayout1.xml.rels       Part-relationship items
        /ppt/slideLayouts/_rels/slideLayout2.xml.rels
        /ppt/slideLayouts/_rels/slideLayout3.xml.rels
        /ppt/slideLayouts/_rels/slideLayout4.xml.rels
        /ppt/slideLayouts/_rels/slideLayout5.xml.rels
        /ppt/slideLayouts/_rels/slideLayout6.xml.rels
        /ppt/slideMasters/slideMaster1.xml                  Slide Master part
        /ppt/slideMasters/_rels/slideMaster1.xml.rels       Part-relationship item
        /ppt/slides/slide1.xml                              Slide parts
        /ppt/slides/slide2.xml
        /ppt/slides/_rels/slide1.xml.rels                   Part-relationship items
        /ppt/slides/_rels/slide2.xml.rels
        /ppt/theme/theme1.xml                               Theme parts
        /ppt/theme/theme2.xml
        /ppt/theme/theme3.xml
        /ppt/theme/themeOverride1.xml                       Theme Override parts
        /ppt/theme/themeOverride2.xml
        /ppt/theme/themeOverride3.xml
        /ppt/theme/themeOverride4.xml
        /ppt/theme/themeOverride5.xml
        /ppt/theme/themeOverride6.xml
        /ppt/theme/themeOverride7.xml
        /ppt/theme/themeOverride8.xml
        /ppt/theme/themeOverride9.xml
        /ppt/theme/themeOverride10.xml
        ```

        The package-relationship item contains the following:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/officeDocument" Target="ppt/presentation.xml"/>
            <Relationship Id="rId3"
                Type="http://…/core-properties" Target="docProps/core.xml"/>
            <Relationship Id="rId2"
                Type="http://…/thumbnail" Target="docProps/thumbnail.wmf"/>
            <Relationship Id="rId4"
                Type="http://…/extended-properties" Target="docProps/app.xml"/>
        </Relationships>
        ```

## 13.3 部件概览

=== "中文"

    从属于该子条款的子条款详细描述了特定于 **PresentationML** 的每个部件类型。

    !!! note info "注意"

        为方便起见，下表总结了这些子条款的信息：

        | **Part**                   | **Relationship Target of**                                          | **Root Element** | **Ref.**   |
        | -------------------------- | ------------------------------------------------------------------- | ---------------- | ---------- |
        | Comment Authors            | Presentation                                                        | cmAuthorLst      | [§13.3.1]  |
        | Comments                   | Slide                                                               | cmLst            | [§13.3.2]  |
        | Handout Master             | Presentation                                                        | handoutMaster    | [§13.3.3]  |
        | Notes Master               | Notes Slide, Presentation                                           | notesMaster      | [§13.3.4]  |
        | Notes Slide                | Slide                                                               | notes            | [§13.3.5]  |
        | Presentation               | PresentationML package                                              | presentation     | [§13.3.6]  |
        | Presentation Properties    | Presentation                                                        | presentationPr   | [§13.3.7]  |
        | Slide                      | Presentation                                                        | sld              | [§13.3.8]  |
        | Slide                      | Layout Slide Master, Notes Slide, Presentation, Slide, Slide Master | sldLayout        | [§13.3.9]  |
        | Slide Master               | Presentation, Slide Layout                                          | sldMaster        | [§13.3.10] |
        | Slide Synchronization Data | Slide                                                               | sldSyncPr        | [§13.3.11] |
        | User-Defined Tags          | Presentation, Slide                                                 | tagLst           | [§13.3.12] |
        | View Properties            | Presentation                                                        | viewPr           | [§13.3.13] |

=== "英文"

    **Part Summary**

    The subclauses subordinate to this one describe in detail each of the part types specific to PresentationML.

    !!! note info "Note"

        For convenience, information from those subclauses is summarized in the following table:

        | **Part**                   | **Relationship Target of**                                          | **Root Element** | **Ref.**   |
        | -------------------------- | ------------------------------------------------------------------- | ---------------- | ---------- |
        | Comment Authors            | Presentation                                                        | cmAuthorLst      | [§13.3.1]  |
        | Comments                   | Slide                                                               | cmLst            | [§13.3.1]  |
        | Handout Master             | Presentation                                                        | handoutMaster    | [§13.3.3]  |
        | Notes Master               | Notes Slide, Presentation                                           | notesMaster      | [§13.3.4]  |
        | Notes Slide                | Slide                                                               | notes            | [§13.3.5]  |
        | Presentation               | PresentationML package                                              | presentation     | [§13.3.6]  |
        | Presentation Properties    | Presentation                                                        | presentationPr   | [§13.3.7]  |
        | Slide                      | Presentation                                                        | sld              | [§13.3.8]  |
        | Slide                      | Layout Slide Master, Notes Slide, Presentation, Slide, Slide Master | sldLayout        | [§13.3.9]  |
        | Slide Master               | Presentation, Slide Layout                                          | sldMaster        | [§13.3.10] |
        | Slide Synchronization Data | Slide                                                               | sldSyncPr        | [§13.3.11] |
        | User-Defined Tags          | Presentation, Slide                                                 | tagLst           | [§13.3.12] |
        | View Properties            | Presentation                                                        | viewPr           | [§13.3.13] |

### 13.3.1 评论作者部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.commentAuthors+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/comments`</td>
        </tr>
    </table>

    此部件类型的实例包含有关向文档添加评论的每位作者的信息。 该信息包括作者姓名、姓名缩写、唯一作者 ID、最后评论索引使用计数以及显示颜色。 （显示评论时可以使用颜色来区分不同作者的评论。）
    
    一个包最多应包含一个评论作者部件。 如果存在，则该部件应成为表示（[§13.3.6]）部件中隐式关系的目标。

    ??? info "Example"

        以下**演示部件关系项**(Presentation part relationship item)包含与评论作者部件的关系，该部件存储在 ZIP 项的 `commentAuthors.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId8"
                Type="http://…/commentAuthors" Target="commentAuthors.xml"/>
        </Relationships>
        ```

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    该内容类型所对应的部件的根元素应为 `cmAuthorLst`.

    !!! info "Example"

        两个人在本文档中发表了评论：`Mary Smith` 和 `Peter Jones`。 她的姓名首字母是“`mas`”，她的作者 ID 是 `0`，她的评论显示颜色索引是 `0`。由于 `Mary` 的最后评论索引使用值为 `3`，因此她要使用的下一个评论索引是 `4`。 他的姓名首字母是“`pjj`”，他的作者 `ID` 是 `1`，他的评论显示颜色索引是 `1`。由于 `Peter` 的最后评论索引使用值为 `1`，因此他要使用的下一个评论索引是 `2`：

        ```xml
        <p:cmAuthorLst xmlns:p="…" …>
            <p:cmAuthor id="0" name="Mary Smith" initials="mas" lastIdx="3"
                clrIdx="0"/>
            <p:cmAuthor id="1" name="Peter Jones" initials="pjj" lastIdx="1"
                clrIdx="1"/>
        </p:cmAuthorLst>
        ```

    注释作者部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为内部）。
    
    注释作者部件不应与 ECMA-376 定义的任何其他部件(Part)有隐式或显式关系。

=== "英文"

    **Comment Authors Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.commentAuthors+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/comments`</td>
        </tr>
    </table>

    An instance of this part type contains information about each author who has added a comment to the document. That information includes the author's name, initials, a unique author-ID, a last-comment-index-used count, and a display color. (The color can be used when displaying comments to distinguish comments from different authors.)
    
    A package shall contain at most one Comment Authors part. If it exists, that part shall be the target of an implicit relationship from the Presentation (§13.3.6) part.

    !!! info "Example"

        The following Presentation part relationship item contains a relationship to the Comment Authors part, which is stored in the ZIP item commentAuthors.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId8"
                Type="http://…/commentAuthors" Target="commentAuthors.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be cmAuthorLst.

    !!! info "Example"

        Two people have authored comments in this document: Mary Smith and Peter Jones. Her initials are "mas", her author-ID is 0, and her comments' display color index is 0. Since Mary's last-comment-index-used value is 3, the next comment-index to be used for her is 4. His initials are "pjj", his author-ID is 1, and his comments' display color index is 1. Since Peter's last-comment-index-used value is 1, the next comment-index to be used for him is 2: 

        ```xml
        <p:cmAuthorLst xmlns:p="…" …>
            <p:cmAuthor id="0" name="Mary Smith" initials="mas" lastIdx="3"
                clrIdx="0"/>
            <p:cmAuthor id="1" name="Peter Jones" initials="pjj" lastIdx="1"
                clrIdx="1"/>
        </p:cmAuthorLst>
        ```

    A Comment Authors part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Comment Authors part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.2 评论部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.comments+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/comments`</td>
        </tr>
    </table>

    此部件类型的实例包含单个幻灯片的评论。 每条评论都通过作者 ID 与其作者相关联。 每个评论的索引号和作者 ID 组合都是唯一的。

    对于包含一个或多个评论的每张幻灯片，包应包含一个评论部件，并且每个部件应是与其相应幻灯片 ([§13.3.8]) 部件的隐式关系的目标。

    !!! info "样例"

        下面的幻灯片部件(Slide Part)的关系项(relationship item) 包含一个到评论部件的关系，该部件存储在 ZIP 项 `../comments/comment2.xml`中:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/comments"
                Target="../comments/comment2.xml"/>
        </Relationships>
        ```

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}
    
    该内容类型所对应的部件的根元素应为 `cmLst`.

    !!! info "样例"

        评论部件包含三条评论，其中两条由一位作者创建，另一条由另一位作者创建，所有评论均显示了评论的日期和时间。 索引号是按每个作者分配的，从 1 开始表示作者的第一条评论：

        ```xml
        <p:cmLst xmlns:p="…" …>
            <p:cm authorId="0" dt="2005-11-13T17:00:22.071" idx="1">
                <p:pos x="4486" y="1342"/>
                <p:text>Comment text goes here.</p:text>
            </p:cm>
            <p:cm authorId="0" dt="2005-11-13T17:00:34.849" idx="2">
                <p:pos x="3607" y="1867"/>
                <p:text>Another comment's text goes here.</p:text>
            </p:cm>
            <p:cm authorId="1" dt="2005-11-15T00:06:46.919" idx="1">
                <p:pos x="1493" y="2927"/>
                <p:text>comment …</p:text>
            </p:cm>
        </p:cmLst>
        ```

    评论部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal`）。

    评论部件不应与 ECMA-376 定义的任何其他部件有隐式或显式的关系。

=== "英文"

    **Comments Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.comments+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/comments`</td>
        </tr>
    </table>

    An instance of this part type contains the comments for a single slide. Each comment is tied to its author via an author-ID. Each comment's index number and author-ID combination are unique.

    A package shall contain one Comments part for each slide containing one or more comments, and each of those parts shall be the target of an implicit relationship from its corresponding Slide ([§13.3.8]) part.

    !!! info "Example"

        The following Slide part-relationship item contains a relationship to a Comments part, which is storedin the ZIP item `../comments/comment2.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/comments"
                Target="../comments/comment2.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be cmLst .

    !!! info "Example"

         The Comments part contains three comments, two created by one author, and one created by another, all at the dates and times shown. The index numbers are assigned on a per-author basis, starting at 1 for an author's first comment:

        ```xml
        <p:cmLst xmlns:p="…" …>
            <p:cm authorId="0" dt="2005-11-13T17:00:22.071" idx="1">
                <p:pos x="4486" y="1342"/>
                <p:text>Comment text goes here.</p:text>
            </p:cm>
            <p:cm authorId="0" dt="2005-11-13T17:00:34.849" idx="2">
                <p:pos x="3607" y="1867"/>
                <p:text>Another comment's text goes here.</p:text>
            </p:cm>
            <p:cm authorId="1" dt="2005-11-15T00:06:46.919" idx="1">
                <p:pos x="1493" y="2927"/>
                <p:text>comment …</p:text>
            </p:cm>
        </p:cmLst>
        ```

    A Comments part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Comments part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.3 讲义母板部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.handoutMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/hnadoutMaster`</td>
        </tr>
    </table>

    此部件类型的实例包含演示文稿讲义上幻灯片、注释、页眉和页脚文本、日期或页码的外观、位置和大小。

    一个包最多应包含一个讲义母板部件，并且它应是演示文稿（[§13.3.6]）部件的显式关系的目标。

    !!! info "Example"

        下面的幻灯片部件(Slide Part)的关系项(relationship item) 包含一个到讲义母板部件的关系，该部件存储在 ZIP 项 `handoutMasters/handoutMaster1.xml`中:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/handoutMaster"
                Target="handoutMasters/handoutMaster1.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `handoutMaster`.

    !!! info "Example"

        ```xml
        <p:handoutMaster xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMap … />
        </p:handoutMaster>
        ```

    讲义母板部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal` ）。

    讲义母板部件允许与 ECMA-376 定义的以下部件具有**隐式关系**：
    
    * 附加特性(Additional Characteristics) ([§15.2.1])
    * 参考书目(Bibliography) ([§15.2.3])
    * 自定义 XML 数据存储(Custom XML Data Storage) ([§15.2.4])
    * 主题(Theme) ([§14.2.7])
    * 缩略图(Thumbnail) ([§15.2.16])

    讲义母版部件允许与 ECMA-376 定义的以下部件有**显式关系**：
    
    * 音频(Audio) ([§15.2.2])
    * 图表(Chart) ([§14.2.1])
    * 内容部件(Content Part) ([§15.2.4])
    * 绘制(Diagrams): 

        * 绘制颜色(Diagram Colors)([§14.2.3]), 
        * 绘制数据(Diagram Data)([§14.2.4]), 
        * 绘制布局定义(Diagram Layout Definition)([§14.2.5]) 和 
        * 绘制样式(Diagram Styles) ([§14.2.6])
  
    * 嵌入式控制持久性(Embedded Control Persistence) ([§15.2.9])
    * 嵌入对象(Embedded Object) ([§15.2.10])
    * 嵌入包(Embedded Package) ([§15.2.11])
    * 超链接(Hyperlink) ([§15.3])
    * 图片(Image) ([§15.2.14])
    * 视频(Video) ([§15.2.15])

    讲义母版部件不应与 ECMA-376 定义的任何其他部件有隐式或显式的关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Handout Master Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.handoutMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/hnadoutMaster`</td>
        </tr>
    </table>

    An instance of this part type contains the look, position, and size of the slides, notes, header and footer text, date, or page number on the presentation's handout.

    A package shall contain at most one Handout Master part, and it shall be the target of an explicit relationship from the Presentation ([§13.3.6]) part.

    !!! info "Example"

        The following Presentation part-relationship item contains a relationship to the Handout Master part, which is stored in the ZIP item handoutMasters/handoutMaster1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/handoutMaster"
                Target="handoutMasters/handoutMaster1.xml"/>
        </Relationships>
        ```
    The root element for a part of this content type shall be handoutMaster

    !!! info "Example"

        ```xml
        <p:handoutMaster xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMap … />
        </p:handoutMaster>
        ```
    
    A Handout Master part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Handout Master part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])
    
    A Handout Master part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors(§14.2.3), Diagram Data(§14.2.4), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3])
    * Image ([§15.2.14])
    * Video ([§15.2.15])
    
    A Handout Master part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.4 笔记母版部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.notesMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/notesMaster`</td>
        </tr>
    </table>

    此部件类型的实例包含有关所有注释页面(notes pages)的内容和格式的信息。

    一个包最多应包含一个 Notes Master 部件，并且该部件应是 Notes Slide ([§13.3.5]) 部件的隐式关系以及**演示部件**(Presentation Part) ([§13.3.5]) 的显式关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](../ecma-part1/chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        以下演示部件关系项包含与 Notes Master 部件的关系，该部件存储在 ZIP 项 `notesMasters/notesMaster1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
            Type="http://…/notesMaster" Target="notesMasters/notesMaster1.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `notesMaster`.

    !!! info "Example"

        ```xml
        <p:notesMaster xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMap … />
        </p:notesMaster>
        ```
    
    Notes Master 部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 `TargetMode` 属性应为 `Internal`）。
    
    Notes Master 部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])

    Notes Master 部件允许与 ECMA-376 定义的以下部件有显式关系：
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: 
  
        * Diagram Colors(§14.2.3), 
        * Diagram Data(§14.2.4), 
        * Diagram Layout Definition([§14.2.5])
        * Diagram Styles ([§14.2.6])
    
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3])
    * Image ([§15.2.14])
    * Video ([§15.2.15])
    
    Notes Master 部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Notes Master Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.notesMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/notesMaster`</td>
        </tr>
    </table>

    An instance of this part type contains information about the content and formatting of all notes pages.
    
    A package shall contain at most one Notes Master part, and that part shall be the target of an implicit relationship from the Notes Slide ([§13.3.5]) part, as well as an explicit relationship from the Presentation ([§13.3.6]) part.

    !!! info "Example"

        The following Presentation part-relationship item contains a relationship to the Notes Master part, which is stored in the ZIP item `notesMasters/notesMaster1.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
            Type="http://…/notesMaster" Target="notesMasters/notesMaster1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be notesMaster.

    !!! info "Example"

        ```xml
        <p:notesMaster xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMap … />
        </p:notesMaster>
        ```
    
    A Notes Master part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Notes Master part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])

    A Notes Master part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors(§14.2.3), Diagram Data(§14.2.4), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3])
    * Image ([§15.2.14])
    * Video ([§15.2.15])
    
    The Notes Master part shall not have implicit or explicit relationships to any other part defined by ECMA-376

### 13.3.5 笔记幻灯片部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.notesSlide+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/notesSlide`</td>
        </tr>
    </table>

    此部件类型的实例包含单个幻灯片的注释。
    
    对于每张包含注释的幻灯片，包应包含一个注释幻灯片部件。 如果存在，则这些部件均应成为幻灯片 ([§13.3.8]) 部件隐式关系的目标。

    !!! info "Example"

        以下演示部件关系项包含与 Notes Slide 部件的关系，该部件存储在 ZIP 项 `../notesSlides/notesSlide1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/notesSlide" Target="../notesSlides/notesSlide1.xml"/>
        </Relationships>
        ```

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    该内容类型所对应的部件的根元素应为 `notes`.

    !!! info "Example"

        The following Slide part-relationship item contains a relationship to a Notes Slide part, which is stored in the ZIP item `../notesSlides/notesSlide1.xml`:

        ```xml
        <p:notes xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMapOvr>
                <a:masterClrMapping/>
            </p:clrMapOvr>
            </p:notes>
        ```
    
    Notes Slide 部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 `TargetMode` 属性应为 `Internal`）。
    
    Notes Slide 部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Notes Master ([§13.3.4])
    * Theme Override([§14.2.8])
    * Thumbnail ([§15.2.16])

    Notes Slide 部件允许与 ECMA-376 定义的以下部件有显式关系：
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    
    * Diagrams: 
  
        * Diagram Colors(§14.2.3), 
        * Diagram Data(§14.2.4), 
        * Diagram Layout Definition([§14.2.5])
        * Diagram Styles ([§14.2.6])
    
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3])
    * Image ([§15.2.14])
    * Video ([§15.2.15])
    
    注释幻灯片部件不得与 ECMA-376 定义的任何其他部件有隐式或显式关系

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Notes Slide Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.notesSlide+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/notesSlide`</td>
        </tr>
    </table>

    An instance of this part type contains the notes for a single slide.
    
    A package shall contain one Notes Slide part for each slide that contains notes. If they exist, those parts shall each be the target of an implicit relationship from the Slide ([§13.3.8]) part.

    !!! info "Example"

        The following Slide part-relationship item contains a relationship to a Notes Slide part, which is stored in the ZIP item `../notesSlides/notesSlide1.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/notesSlide" Target="../notesSlides/notesSlide1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be notes.

    !!! info "Example"

        The following Slide part-relationship item contains a relationship to a Notes Slide part, which is stored in the ZIP item `../notesSlides/notesSlide1.xml`:

        ```xml
        <p:notes xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMapOvr>
                <a:masterClrMapping/>
            </p:clrMapOvr>
            </p:notes>
        ```
    
    A Notes Slide part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Notes Slide part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Notes Master ([§13.3.4])
    * Theme Override([§14.2.8])
    * Thumbnail ([§15.2.16])

    A Notes Slide part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors(§14.2.3), Diagram Data(§14.2.4), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3])
    * Image ([§15.2.14])
    * Video ([§15.2.15])
    
    The Notes Slide part shall not have implicit or explicit relationships to any other part defined by ECMA-376

### 13.3.6 演示部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.presentation.main+xml` </br>
                `application/vnd.openxmlformats-officedocument.presentationml.slideshow.main+xml` </br>
                `application/vnd.openxmlformats-officedocument.presentationml.template.main+xml` 
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument`</td>
        </tr>
    </table>

    此部件类型的实例包含幻灯片演示文稿的定义。
    
    一个包应恰好包含一个演示部件(Presentation part)，并且该部件应是包关系项中关系的目标。

    !!! info "Example"

        以下 `PresentationML` 的包关系项包含与 `Presentation` 部件的关系，该部件存储在ZIP 项 `ppt/presentation.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/officeDocument" Target="ppt/presentation.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `presentation`.

    !!! info "Example"

        This presentation contains two slides:

        ```xml
        <p:presentation xmlns:p="…" … >
            <p:sldMasterIdLst>
                <p:sldMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId1"/>
            </p:sldMasterIdLst>
            <p:notesMasterIdLst>
                <p:notesMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId4"/>
            </p:notesMasterIdLst>
            <p:handoutMasterIdLst>
                <p:handoutMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId5"/>
            </p:handoutMasterIdLst>
            <p:sldIdLst>
                <p:sldId id="267"
                    xmlns:rel="http://…/relationships" rel:id="rId2"/>
                <p:sldId id="256"
                    xmlns:rel="http://…/relationships" rel:id="rId3"/>
            </p:sldIdLst>
            <p:sldSz cx="9144000" cy="6858000"/>
            <p:notesSz cx="6858000" cy="9144000"/>
        </p:presentation>
        ```
    
    演示部件(Presentation part)应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal`）。

    允许演示部件(Presentation part)与 ECMA-376 定义的以下部件有隐式关系：
    
    * Additional Characteristics ([§15.2.1])
    * Comment Authors ([§13.3.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Font ([§15.2.13])
    * Presentation Properties ([§13.3.7])
    * Table Styles ([§14.2.9])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])
    * View Properties ([§13.3.13]).
    
    演示部件(Presentation part)允许与 ECMA-376 定义的以下部件有显式关系：
    
    * Notes Master ([§13.3.4])
    * Handout Master ([§13.3.3])
    * Slide ([§13.3.8])
    * Slide Master ([§13.3.10])
    * User Defined Tags ([§13.3.12])

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Presentation Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.presentation.main+xml` </br>
                `application/vnd.openxmlformats-officedocument.presentationml.slideshow.main+xml` </br>
                `application/vnd.openxmlformats-officedocument.presentationml.template.main+xml` 
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument`</td>
        </tr>
    </table>

    An instance of this part type contains the definition for a slide presentation.
    
    A package shall contain exactly one Presentation part, and that part shall be the target of a relationship in the package-relationship item.

    !!! info "Example"

        The following PresentationML's package-relationship item contains a relationship to the Presentation part, which is stored in the ZIP item ppt/presentation.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/officeDocument" Target="ppt/presentation.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be presentation.

    !!! info "Example"

        This presentation contains two slides:

        ```xml
        <p:presentation xmlns:p="…" … >
            <p:sldMasterIdLst>
                <p:sldMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId1"/>
            </p:sldMasterIdLst>
            <p:notesMasterIdLst>
                <p:notesMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId4"/>
            </p:notesMasterIdLst>
            <p:handoutMasterIdLst>
                <p:handoutMasterId
                    xmlns:rel="http://…/relationships" rel:id="rId5"/>
            </p:handoutMasterIdLst>
            <p:sldIdLst>
                <p:sldId id="267"
                    xmlns:rel="http://…/relationships" rel:id="rId2"/>
                <p:sldId id="256"
                    xmlns:rel="http://…/relationships" rel:id="rId3"/>
            </p:sldIdLst>
            <p:sldSz cx="9144000" cy="6858000"/>
            <p:notesSz cx="6858000" cy="9144000"/>
        </p:presentation>
        ```
    
    A Presentation part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Presentation part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Comment Authors ([§13.3.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Font ([§15.2.13])
    * Presentation Properties ([§13.3.7])
    * Table Styles ([§14.2.9])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])
    * View Properties ([§13.3.13]).
    
    A Presentation part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Notes Master ([§13.3.4])
    * Handout Master ([§13.3.3])
    * Slide ([§13.3.8])
    * Slide Master ([§13.3.10])
    * User Defined Tags ([§13.3.12])

### 13.3.7 演示属性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.presProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/presProps`</td>
        </tr>
    </table>

    此部件类型的实例包含演示文稿(presentation)的所有属性。
    
    包应恰好包含一个演示文稿属性(Presentation Properties)部件，并且该部件应是来自幻灯片部件(Presentation Part)（[§13.3.6]）的隐式关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        以下演示部件关系项包含与演示文稿属性(Presentation Properties)部件的关系，该部件存储在 ZIP 项 `presProps.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http`://…/presProps" Target="presProps.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `presentationPr`.

    !!! info "Example"

        ```xml
        <p:presentationPr xmlns:p="…" …>
            <p:clrMru>
                …
            </p:clrMru>
            …
        </p:presentationPr>
        ```
    
    演示文稿属性(Presentation Properties)部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal` ）。
    
    演示文稿属性(Presentation Properties)部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Presentation Properties Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.presProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/presProps`</td>
        </tr>
    </table>

    An instance of this part type contains all the presentation's properties.
    
    A package shall contain exactly one Presentation Properties part, and that part shall be the target of an implicit relationship from the Presentation (§13.3.6) part.

    !!! info "Example"

        The following Presentation part-relationship item contains a relationship to the Presentation Properties part, which is stored in the ZIP item presProps.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http`://…/presProps" Target="presProps.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be presentationPr.

    !!! info "Example"

        ```xml
        <p:presentationPr xmlns:p="…" …>
            <p:clrMru>
                …
            </p:clrMru>
            …
        </p:presentationPr>
        ```
    
    A Presentation Properties part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Presentation Properties part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.8 幻灯片部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slide+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slide`</td>
        </tr>
    </table>

    幻灯片部件(Slide Part)包含单张幻灯片的内容。
    
    包中每张幻灯片应包含一个幻灯片部件(Slide Part)，并且每个部件均应是演示文稿 ([§13.3.6]) 部件中显式关系的目标。

    !!! info "Example"

        考虑具有两张幻灯片的 `PresentationML` 文档。 相应的演示部件关系项包含与幻灯片部件的两个关系，它们存储在 ZIP 项 `slides/slide1.xml`和`slides/slide2.xml`中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/slide" Target="slides/slide1.xml"/>
            <Relationship Id="rId3"
                Type="http://…/slide" Target="slides/slide2.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `sld`.


    !!! info "Example"

         slides/slide1.xml contains:

        ```xml
        <p:sld xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMapOvr>
            …
            </p:clrMapOvr>
            <p:timing>
                <p:tnLst>
                    <p:par>
                        <p:cTn id="1" dur="indefinite" restart="never" nodeType="tmRoot"/>
                    </p:par>
                </p:tnLst>
            </p:timing>
        </p:sld>
        ```
    
    幻灯片部件(Slide Part)应位于包含关系部件的包内（从语法上表达，Relationship 元素的 `TargetMode` 属性应为 `Internal`）。

    允许 幻灯片部件(Slide Part)与 ECMA-376 定义的以下部件具有隐式关系：

    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Comments ([§13.3.2])
    * Custom XML Data Storage ([§15.2.4])
    * Notes Slide ([§13.3.5])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])
    * Slide Layout ([§13.3.9])
    * Slide Synchronization Data ([§13.3.11])

    允许 幻灯片部件(Slide Part)与 ECMA-376 定义的以下部件有显式关系：

    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: 
  
        * Diagram Colors(§14.2.3), 
        * Diagram Data(§14.2.4), 
        * Diagram Layout Definition([§14.2.5])
        * Diagram Styles ([§14.2.6])
    
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * User Defined Tags ([§13.3.12])
    * Video ([§15.2.15])

    幻灯片部件(Slide Part)不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Slide Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slide+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slide`</td>
        </tr>
    </table>

    A Slide part contains the contents of a single slide.
    
    A package shall contain one Slide part per slide, and each of those parts shall be the target of an explicit relationship from the Presentation (§13.3.6) part.

    !!! info "Example"

        Consider a PresentationML document having two slides. The corresponding Presentation partrelationship item contains two relationships to Slide parts, which are stored in the ZIP items `slides/slide1.xml` and `slides/slide2.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/slide" Target="slides/slide1.xml"/>
            <Relationship Id="rId3"
                Type="http://…/slide" Target="slides/slide2.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be sld.

    !!! info "Example"

         slides/slide1.xml contains:

        ```xml
        <p:sld xmlns:p="…">
            <p:cSld name="">
            …
            </p:cSld>
            <p:clrMapOvr>
            …
            </p:clrMapOvr>
            <p:timing>
                <p:tnLst>
                    <p:par>
                        <p:cTn id="1" dur="indefinite" restart="never" nodeType="tmRoot"/>
                    </p:par>
                </p:tnLst>
            </p:timing>
        </p:sld>
        ```
    
    A Slide part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Slide part is permitted to have implicit relationships to the following parts defined by ECMA-376:

    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Comments ([§13.3.2])
    * Custom XML Data Storage ([§15.2.4])
    * Notes Slide ([§13.3.5])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])
    * Slide Layout ([§13.3.9])
    * Slide Synchronization Data ([§13.3.11])

    A Slide part is permitted to have explicit relationships to the following parts defined by ECMA-376:

    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data(§14.2.4), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * User Defined Tags ([§13.3.12])
    * Video ([§15.2.15])

    A Slide part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.9 幻灯片布局部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideLayout+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideLayout`</td>
        </tr>
    </table>

    此部件类型的实例包含此演示文稿的**幻灯片布局模板**(slide layout template)的定义。 此模板定义创建此幻灯片类型时绘图对象的默认外观和位置。
    
    包应包含一个或多个幻灯片布局部件，并且每个部件应是幻灯片母版 ([§13.3.10]) 部件中显式关系的目标，以及来自每个幻灯片 ( [§13.3.8]) 与此幻灯片布局相关的部件。

    !!! info "Example"

        以下幻灯片母版部件关系项目包含与多个幻灯片布局部件的关系，这些部件存储在 ZIP 项目 `../slideLayouts/slideLayoutN.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout1.xml"/>
            <Relationship Id="rId2"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout2.xml"/>
            <Relationship Id="rId3"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout3.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `sldLayout`.

    !!! info "Example"

        ```xml
        <p:sldLayout xmlns:p="…" matchingName="" type="title" preserve="1">
            <p:cSld name="Title Slide">
                …
            </p:cSld>
            <p:clrMapOvr>
                <a:masterClrMapping/>
            </p:clrMapOvr>
            <p:timing/>
            </p:sldLayout>
        </p:sldMaster>
        ```
    
    幻灯片布局部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Slide Master ([§13.3.10])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])

    幻灯片布局部件允许与 ECMA-376 定义的以下部件有显式关系：
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: 
  
        * Diagram Colors(§14.2.3), 
        * Diagram Data(§14.2.4), 
        * Diagram Layout Definition([§14.2.5])
        * Diagram Styles ([§14.2.6])
    
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * Video ([§15.2.15])

    幻灯片布局部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Slide Layout Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideLayout+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideLayout`</td>
        </tr>
    </table>

    An instance of this part type contains the definition for a slide layout template for this presentation. This template defines the default appearance and positioning of drawing objects on this slide type when it is created.
    
    A package shall contain one or more Slide Layout parts, and each of those parts shall be the target of an explicit relationship in the Slide Master ([§13.3.10]) part, as well as an implicit relationship from each of the Slide ([§13.3.8]) parts associated with this slide layout.

    !!! info "Example"

         The following Slide Master part-relationship item contains relationships to several Slide Layout parts, which are stored in the ZIP items ../slideLayouts/slideLayoutN.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout1.xml"/>
            <Relationship Id="rId2"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout2.xml"/>
            <Relationship Id="rId3"
                Type="http://…/slideLayout"
                Target="../slideLayouts/slideLayout3.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be sldLayout.

    !!! info "Example"

        ```xml
        <p:sldLayout xmlns:p="…" matchingName="" type="title" preserve="1">
            <p:cSld name="Title Slide">
                …
            </p:cSld>
            <p:clrMapOvr>
                <a:masterClrMapping/>
            </p:clrMapOvr>
            <p:timing/>
            </p:sldLayout>
        </p:sldMaster>
        ```
    
    A Slide Layout part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Slide Master ([§13.3.10])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])

    A Slide Layout part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * Video ([§15.2.15])

    A Slide Layout part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.10 幻灯片母版部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideMaster`</td>
        </tr>
    </table>

    此部件类型的实例包含格式、文本和对象的主定义，这些定义出现在从该幻灯片母版派生的演示文稿中的每张幻灯片上。

    包应包含一个或多个**幻灯片母版部件**(Slide Master parts)([§13.3.10])，每个部件都应是**演示部件**(Presentation part)([§13.3.6])的显式关系的目标，以及任何**幻灯片布局部件**(Slide Layout part)([§13.3.9])的隐式关系目标（其中幻灯片布局是基于此**幻灯片母版**定义的）。 每一个**幻灯片母板部件**([§13.3.10])也可以选择成为**幻灯片布局部件**(Slide Layout part)([§13.3.9])中关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        以下演示文稿部件关系项包含与幻灯片母版部件的关系，该部件存储在 ZIP 项 `slipMasters/slideMaster1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideMaster" Target="slideMasters/slideMaster1.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `sldMaster`.

    !!! info "Example"

        ```xml
        <p:sldMaster xmlns:p="…">
            <p:cSld name="">
                …
            </p:cSld>
            <p:clrMap … />
        </p:sldMaster>
        ```
    
    幻灯片母版部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为`Internal`）。

    幻灯片母版部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])
    
    允许幻灯片母版部件与 ECMA-376 定义的以下部件有显式关系：
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: 
  
        * Diagram Colors(§14.2.3), 
        * Diagram Data(§14.2.4), 
        * Diagram Layout Definition([§14.2.5])
        * Diagram Styles ([§14.2.6])
    
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * Slide Layout ([§13.3.9])
    * Video ([§15.2.15])
    
    幻灯片母版部件不得与 ECMA-376 定义的任何其他部件有隐式或显式关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Slide Master Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideMaster+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideMaster`</td>
        </tr>
    </table>

    An instance of this part type contains the master definition of formatting, text, and objects that appear on each slide in the presentation that is derived from this slide master.
    
    A package shall contain one or more Slide Master parts, each of which shall be the target of an explicit relationship from the Presentation ([§13.3.6]) part, as well as an implicit relationship from any Slide Layout ([§13.3.9]) part where that slide layout is defined based on this slide master. Each can optionally be the target of a relationship in a Slide Layout ([§13.3.9]) part as well.

    !!! info "Example"

         The following Presentation part-relationship item contains a relationship to the Slide Master part, which is stored in the ZIP item slideMasters/slideMaster1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideMaster" Target="slideMasters/slideMaster1.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be sldMaster.

    !!! info "Example"

        ```xml
        <p:sldMaster xmlns:p="…">
            <p:cSld name="">
                …
            </p:cSld>
            <p:clrMap … />
        </p:sldMaster>
        ```
    
    A Slide Master part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Slide Master part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Custom XML Data Storage ([§15.2.4])
    * Theme Override ([§14.2.8])
    * Thumbnail ([§15.2.16])
    
    A Slide Master part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Audio ([§15.2.2])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlink ([§15.3]).
    * Image ([§15.2.14])
    * Slide Layout ([§13.3.9])
    * Video ([§15.2.15])
    
    A Slide Master part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.11 幻灯片同步数据部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideUpdateInfo+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideUpdateInfo`</td>
        </tr>
    </table>

    此部件类型的实例包含指定幻灯片当前状态的属性，该幻灯片与存储在中央服务器上的幻灯片版本同步。
    
    对于存储在演示文稿中的每张幻灯片，包应包含零个或一个幻灯片同步数据部件，并且该部件应是来自相应幻灯片部件 ([§13.3.8]) 的隐式关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        以下幻灯片部件关系项包含与幻灯片同步数据部件的关系，该部件存储在 ZIP 项 `slipUpdateInfo/slideUpdateInfo1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" Type="http://…/slideUpdateInfo"
                Target="slideUpdateInfo/slideUpdateInfo1.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `sldSyncPr`.

    !!! info "Example"

        ```xml
        <p:sldSyncPr xmlns:p="…" serverSldId="1"
            serverSldModifiedTime="2006-08-12T01:31:08"
            clientInsertedTime="2006-08-12T01:34:11.227" />
        ```
    
    幻灯片同步数据部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为`Internal`）。

    幻灯片同步数据部件允许与 ECMA-376 定义的以下部件具有隐式关系：

    * Slide Synchronization Server Location ([§13.4])

    幻灯片同步数据部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

=== "英文"

    **Slide Synchronization Data Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.slideUpdateInfo+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideUpdateInfo`</td>
        </tr>
    </table>

    An instance of this part type contains properties specifying the current state of a slide that is being synchronized with a version of that slide stored on a central server.
    
    A package shall contain zero or one Slide Synchronization Data part for each slide stored in the presentation, and that part shall be the target of an implicit relationship from the corresponding Slide ([§13.3.8]) part.

    !!! info "Example"

        The following Slide part-relationship item contains a relationship to the Slide Synchronization Data part, which is stored in the ZIP item slideUpdateInfo/slideUpdateInfo1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" Type="http://…/slideUpdateInfo"
                Target="slideUpdateInfo/slideUpdateInfo1.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be sldSyncPr.

    !!! info "Example"

        ```xml
        <p:sldSyncPr xmlns:p="…" serverSldId="1"
            serverSldModifiedTime="2006-08-12T01:31:08"
            clientInsertedTime="2006-08-12T01:34:11.227" />
        ```
    
    A Slide Synchronization Data part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Slide Synchronization Data part is permitted to have implicit relationships to the following parts defined by ECMA-376:

    * Slide Synchronization Server Location ([§13.4])

    A Slide Synchronization Data part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.12  用户已定义标签部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.tags+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/tags`</td>
        </tr>
    </table>

    此部件类型的实例包含演示文稿中对象的一组用户定义属性（每个属性由名称/值对组成）。
    
    包应包含零个或多个用户定义标签部件，每个部件作为相应演示文稿 ([§13.3.6]) 或幻灯片 ([§13.3.8]) 部件的显式关系的目标。

    !!! info "Example"

        以下幻灯片部件关系项包含与用户定义标签部件的关系，该部件存储在 ZIP 项 `tags/tag1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" Type="http://…/tag"
                Target="tags/tag1.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `tagLst`.

    !!! info "Example"

        ```xml
        <p:tagLst xmlns:p="…" >
            <p:tag name="testTagName" val="testTagValue" />
        </p:tagLst>
        ```
    
    用户定义标签部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为`Internal`）。

    用户定义标签部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **User Defined Tags Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.tags+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/tags`</td>
        </tr>
    </table>

    An instance of this part type contains a set of user-defined properties for an object in a presentation (each property consisting of a name/value pair).
    
    A package shall contain zero or more User Defined Tags parts, each as the target of an explicit relationship from the corresponding Presentation ([§13.3.6]) or Slide ([§13.3.8]) part.

    !!! info "Example"

        以下幻灯片部件关系项包含与用户定义标签部件的关系，该部件存储在 ZIP 项 `tags/tag1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1" Type="http://…/tag"
                Target="tags/tag1.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be tagLst.

    !!! info "Example"

        ```xml
        <p:tagLst xmlns:p="…" >
            <p:tag name="testTagName" val="testTagValue" />
        </p:tagLst>
        ```
    
    A User Defined Tags part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A User Defined Tags part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 13.3.13 视图属性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.viewProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/viewProps`</td>
        </tr>
    </table>

    此部件类型的实例包含此演示文稿的视图属性。
    
    包应包含零个或一个“视图属性”部件，如果存在，则该部件应是来自“演示”([§13.3.6]) 部件的隐式关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        以下演示部件关系项包含与视图属性部件的关系，该部件存储在 ZIP 项 `viewProps.xml` 中：
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId7"
            Type="http://…/viewProps" Target="viewProps.xml"/>
        </Relationships>
        ```

    该内容类型所对应的部件的根元素应为 `viewPr`.

    !!! info "Example"

        ```xml
        <p:viewPr xmlns:p="…" …>
            <p:normalViewPr showOutlineIcons="0">
                …
            </p:normalViewPr>
            <p:slideViewPr>
                …
            </p:slideViewPr>
            <p:outlineViewPr>
                …
            </p:outlineViewPr>
            <p:notesTextViewPr>
                …
            </p:notesTextViewPr>
            <p:gridSpacing cx="78028800" cy="78028800"/>
        </p:viewPr>
        ```
    
    视图属性部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为`Internal`）。

    视图属性部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **View Properties Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.presentationml.viewProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/presentationml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/viewProps`</td>
        </tr>
    </table>

    An instance of this part type contains display properties for this presentation.
    
    A package shall contain zero or one View Properties part, and if it exists, that part shall be the target of an implicit relationship from the Presentation ([§13.3.6]) part.

    !!! info "Example"

        The following Presentation part-relationship item contains a relationship to the View Properties part, which is stored in the ZIP item viewProps.xml:
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId7"
            Type="http://…/viewProps" Target="viewProps.xml"/>
        </Relationships>
        ```
    The root element for a part of this content type shall be viewPr.

    !!! info "Example"

        ```xml
        <p:viewPr xmlns:p="…" …>
            <p:normalViewPr showOutlineIcons="0">
                …
            </p:normalViewPr>
            <p:slideViewPr>
                …
            </p:slideViewPr>
            <p:outlineViewPr>
                …
            </p:outlineViewPr>
            <p:notesTextViewPr>
                …
            </p:notesTextViewPr>
            <p:gridSpacing cx="78028800" cy="78028800"/>
        </p:viewPr>
        ```
    
    A View Properties part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A View Properties part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

## 13.4 HTML 发布位置

=== "中文"

    <table border=1>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/htmlPubSaveAs`</td>
        </tr>
    </table>

    当演示文稿指定可以将 HTML 格式的可选副本推送到的外部位置时，应使用此关系来确定演示文稿的 HTML 副本发布的目标位置。

    包应包含与 HTML 发布位置链接的每张幻灯片的一个 HTML 发布位置关系，并且该关系应是来自相应演示文稿属性（[§13.3.7]）部件的显式关系。

    !!! info "Example"

        存储 <http://www.openxmlformats.org/test.htm> HTML 发布位置的演示属性部件在该部件的关系部件中包含以下关系：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/htmlPubSaveAs"
                Target="http://www.openxmlformats.org/test.htm" type=”External”/>
        </Relationships>
        ```
    
    HTML 发布位置应位于包含关系部件的包的外部（从语法上表达，关系元素的 TargetMode 属性应为 `External` ）。

=== "英文"

    **HTML Publish Location**

    <table border=1>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/htmlPubSaveAs`</td>
        </tr>
    </table>

    When a presentation specifies an external location to which an optional copy might be pushed in the HTML format, this relationship shall be used to target the location where the HTML copy of the presentation is published.

    A package shall contain one HTML Publish Location relationship for each slide linked with an HTML publish location, and that relationships shall be an explicit relationship from the corresponding Presentation Properties (§13.3.7) part.

    !!! info "Example"

        A Presentation Properties part, which stores an HTML Publish Location of <http://www.openxmlformats.org/test.htm> contains the following relationship in that part's relationship part:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/htmlPubSaveAs"
                Target="http://www.openxmlformats.org/test.htm" type=”External”/>
        </Relationships>
        ```
    
    An HTML publish location shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

## 13.5 幻灯片同步服务器位置

=== "中文"

    Source Relationship
    : `http://purl.oclc.org/ooxml/officeDocument/relationships/slideUpdateUrl`

    <table border=1>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideUpdateUrl`</td>
        </tr>
    </table>

    当幻灯片与远程服务器上存储的副本同步时，应使用此关系来确定幻灯片的服务器副本的存储位置。
    
    包应包含与服务器数据链接的每张幻灯片的一个幻灯片同步服务器位置关系，并且该关系应是来自相应幻灯片同步数据（[§13.3.11]）部件的隐式关系。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"

        存储有关与位于 <http://www.openxmlformats.org/slides/> 的服务器同步的幻灯片信息的幻灯片同步数据部件在该部件的关系部件项中包含以下关系：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideupdateUrl"
                Target="http://www.openxmlformats.org/slides/" type=”External”/>
        </Relationships>
        ```

    幻灯片同步服务器位置应位于包含关系部件的包的外部（从语法上表达，关系元素的 TargetMode 属性应为`External`）。

=== "英文"

    **Slide Synchronization Server Location**

    <table border=1>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/slideUpdateUrl`</td>
        </tr>
    </table>

    When a slide is being synchronized with a copy stored on a remote server, this relationship shall be used to target the location where the server copy of the slide is stored.
    
    A package shall contain one Slide Synchronization Server Location relationship for each slide linked with server data, and that relationships shall be an implicit relationship from the corresponding Slide Synchronization Data ([§13.3.11]) part.

    !!! info "Example"

        A Slide Synchronization Data part that stores information about a slide that is synchronized with a server located at <http://www.openxmlformats.org/slides/> contains the following relationship in that part's relationship part item:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/slideupdateUrl"
                Target="http://www.openxmlformats.org/slides/" type=”External”/>
        </Relationships>
        ```

    A slide synchronization server location shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

<!-- 链接定义 -->

[§13.3.1]: #1331-评论作者部件
[§13.3.2]: #1332-评论部件
[§13.3.3]: #1333-讲义母板部件
[§13.3.4]: #1334-笔记母版部件
[§13.3.5]: #1335-笔记幻灯片部件
[§13.3.6]: #1336-演示部件
[§13.3.7]: #1337-演示属性部件
[§13.3.8]: #1338-幻灯片部件
[§13.3.9]: #1339-幻灯片布局部件
[§13.3.10]: #13310-幻灯片母版部件
[§13.3.11]: #13311-幻灯片同步数据部件
[§13.3.12]: #13312--用户已定义标签部件
[§13.3.13]: #13313-视图属性部件

[§14]: ./chapter-14.md#14-drawingml
[§14.1]: ./chapter-14.md#141-drawingml-特定术语词汇表
[§14.2]: ./chapter-14.md#142-部件概览
[§14.2.1]: ./chapter-14.md#1421-图表部件
[§14.2.2]: ./chapter-14.md#1422-图表绘制部件
[§14.2.3]: ./chapter-14.md#1423-绘制颜色部件
[§14.2.4]: ./chapter-14.md#1424-绘制数据部件
[§14.2.5]: ./chapter-14.md#1425-绘制布局定义部件
[§14.2.6]: ./chapter-14.md#1426-绘制样式部件
[§14.2.7]: ./chapter-14.md#1427-主题部件
[§14.2.8]: ./chapter-14.md#1428-主题覆盖部件
[§14.2.9]: ./chapter-14.md#1429-表格样式部件

[§15]: ./chapter-15.md#15-共享
[§15.1]: ./chapter-15.md#151-共享术语词汇表
[§15.2]: ./chapter-15.md#152-部件概览
[§15.2.1]: ./chapter-15.md#1521-附加特性部件
[§15.2.2]: ./chapter-15.md#1522-音频部件
[§15.2.3]: ./chapter-15.md#1523-参考文献部件
[§15.2.4]: ./chapter-15.md#1524-内容部件
[§15.2.5]: ./chapter-15.md#1525-自定义xml数据存储部件
[§15.2.6]: ./chapter-15.md#1526-自定义-xml-数据存储属性部件
[§15.2.7]: ./chapter-15.md#1527-数字签名起源部件
[§15.2.8]: ./chapter-15.md#1528-数字签名-xml-签名部件
[§15.2.9]: ./chapter-15.md#1529-嵌入式控制持久化部件
[§15.2.10]: ./chapter-15.md#15210-嵌入对象部件
[§15.2.11]: ./chapter-15.md#15211-嵌入包部件
[§15.2.12]: ./chapter-15.md#15212-文件属性部件
[§15.2.12.1]: ./chapter-15.md#152121-核心文件属性部件
[§15.2.12.2]: ./chapter-15.md#152122-自定义文件属性部件
[§15.2.12.3]: ./chapter-15.md#152123-扩展文件属性部件
[§15.2.13]: ./chapter-15.md#15213-字体部件
[§15.2.14]: ./chapter-15.md#15214-图片部件
[§15.2.15]: ./chapter-15.md#15215-打印机设置部件
[§15.2.16]: ./chapter-15.md#15216-缩略图部件
[§15.2.17]: ./chapter-15.md#15217-视频部件
[§15.3]: ./chapter-15.md#153-超链接
