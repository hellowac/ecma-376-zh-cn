# 14. DrawingML

=== "中文"

    本节中定义的关系项和部件由 WordprocessingML ([§11])、SpreadsheetML ([§12]) 和PresentationML ([§13]) 环境中的一个或多个使用。

=== "英文"

    **DrawingML**

    The relationship items and parts defined in this clause are used by one or more of WordprocessingML ([§11]), SpreadsheetML ([§12]), and PresentationML ([§13]) environments.

## 14.1 DrawingML 特定术语词汇表

=== "中文"

    **diagram** — 使用一组相关的颜色、数据、布局和样式部件显示的图片或图形表示形式。 图表类型的示例有循环图、组织图、金字塔图、目标图和维恩图。

=== "英文"

    **Glossary of DrawingML-Specific Terms**

    **diagram** — A picture or graphical representation that is displayed using a related set of color, data, layout, and style parts. Examples of diagram types are cycle, organization chart, pyramid, target, and Venn.

## 14.2 部件概览

=== "中文"

    从属于该子约定的子章节详细描述了 DrawingML 特有的每种部件类型。

    ??? info "Note"
    
        为方便起见，下表总结了这些子章节的信息:

        <table>
            <thead>
                <tr>
                    <th> **Part** </th>
                    <th> **Relationship Target of** </th>
                    <th> **Root Element** </th>
                    <th> **Ref.** </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td> Chart </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                        All: Chart Drawing <br/> 
                    </td>
                    <td> chartSpace </td>
                    <td> [§14.2.1] </td>
                </tr>
                <tr>
                    <td> Chart Drawing </td>
                    <td> 
                        All: Chart
                    </td>
                    <td> userShapes </td>
                    <td> [§14.2.2] </td>
                </tr>
                <tr>
                    <td> Diagram Colors </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> colorsDef </td>
                    <td> [§14.2.3] </td>
                </tr>
                <tr>
                    <td> Diagram Data </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> dataModel </td>
                    <td> [§14.2.4] </td>
                </tr>
                <tr>
                    <td> Diagram Layout Definition </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> layoutDef </td>
                    <td> [§14.2.5] </td>
                </tr>
                <tr>
                    <td> Diagram Style </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> styleDef </td>
                    <td> [§14.2.6] </td>
                </tr>
                <tr>
                    <td> Theme </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Workbook <br/> 
                        PresentationML:  Handout Master, Notes Master, <br/> 
                        Presentation, Slide Master 
                    </td>
                    <td> theme </td>
                    <td> [§14.2.7] </td>
                </tr>
                <tr>
                    <td> Theme Override </td>
                    <td> 
                        PresentationML: Notes Slide, Slide, Slide Layout
                    </td>
                    <td> themeOverride </td>
                    <td> [§14.2.8] </td>
                </tr>
                <tr>
                    <td> Table Styles </td>
                    <td> 
                        PresentationML: Presentation
                    </td>
                    <td> tblStyleLst </td>
                    <td> [§14.2.9] </td>
                </tr>
            </tbody>
        </table>

=== "英文"

    **Part Summary**

    The subclauses subordinate to this one describe in detail each of the part types specific to DrawingML.

    ??? info "Note"
    
        For convenience, information from those subclauses is summarized in the following table:

        <table>
            <thead>
                <tr>
                    <th> **Part** </th>
                    <th> **Relationship Target of** </th>
                    <th> **Root Element** </th>
                    <th> **Ref.** </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td> Chart </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                        All: Chart Drawing <br/> 
                    </td>
                    <td> chartSpace </td>
                    <td> [§14.2.1] </td>
                </tr>
                <tr>
                    <td> Chart Drawing </td>
                    <td> 
                        All: Chart
                    </td>
                    <td> userShapes </td>
                    <td> [§14.2.2] </td>
                </tr>
                <tr>
                    <td> Diagram Colors </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> colorsDef </td>
                    <td> [§14.2.3] </td>
                </tr>
                <tr>
                    <td> Diagram Data </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> dataModel </td>
                    <td> [§14.2.4] </td>
                </tr>
                <tr>
                    <td> Diagram Layout Definition </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> layoutDef </td>
                    <td> [§14.2.5] </td>
                </tr>
                <tr>
                    <td> Diagram Style </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Drawings <br/> 
                        PresentationML: Handout Master, Notes Master, <br/> 
                        Notes Slide, Slide Layout, Slide Master, Slide <br/> 
                    </td>
                    <td> styleDef </td>
                    <td> [§14.2.6] </td>
                </tr>
                <tr>
                    <td> Theme </td>
                    <td> 
                        WordprocessingML: Main Document <br/> 
                        SpreadsheetML: Workbook <br/> 
                        PresentationML:  Handout Master, Notes Master, <br/> 
                        Presentation, Slide Master 
                    </td>
                    <td> theme </td>
                    <td> [§14.2.7] </td>
                </tr>
                <tr>
                    <td> Theme Override </td>
                    <td> 
                        PresentationML: Notes Slide, Slide, Slide Layout
                    </td>
                    <td> themeOverride </td>
                    <td> [§14.2.8] </td>
                </tr>
                <tr>
                    <td> Table Styles </td>
                    <td> 
                        PresentationML: Presentation
                    </td>
                    <td> tblStyleLst </td>
                    <td> [§14.2.9] </td>
                </tr>
            </tbody>
        </table>

### 14.2.1 图表部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.viewProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/chart`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/chart`</td>
        </tr>
    </table>

    此部件类型的实例描述了一个图表。

    包应包含文档中每个图表的图表部件。 
    
    在 WordprocessingML 文档中，每个此类部件应是主文档 ([§11.3.10]) 部件中显式关系的目标。 
    
    在 SpreadsheetML 文档中，每个此类部件应是绘图 ([§12.3.8]) 部件中显式关系的目标。 
    
    在 PresentationML 文档中，每个此类部件应是
    
    - 讲义母版（[§13.3.3]）、
    - 注释母版（[§13.3.4]）、
    - 注释幻灯片（[§13.3.5]）
    - 幻灯片 ([§13.3.8])、
    - 幻灯片布局 ([§13.3.9]) 
    - 幻灯片母版 ([§13.3.10]) 
    
    等的显式关系的目标。

    如果指向此图表绘图部件的图表是图表表部件中关系的目标，则也允许此部件作为
    
    - 图表绘图 ([§14.2.2]) 部件
    
    中显式关系的目标。 
    
    换句话说，图表可以嵌入另一个图表, 唯一的限制是父级图表需是 `chartsheet` 的部件。

    ??? info "Example"

        以下主文档部件关系项包含与两个图表部件的关系，这些部件存储在 ZIP 项 `../charts/chartN.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/chart" Target="charts/chart1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/chart" Target="charts/chart2.xml"/>
        </Relationships>
        ```

        以下绘图部件关系项包含与图表部件的关系，该部件存储在 ZIP 项 `../charts/chart1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/relationships/chart" Target="../charts/chart1.xml"/>
        </Relationships>
        ```

        以下幻灯片部件关系项包含与两个图表部件的关系，这些部件存储在 ZIP 项 `../charts/chartN.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/chart" Target="../charts/chart1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/chart" Target="../charts/chart2.xml"/>
        </Relationships>
        ```

    该内容类型的一部件的根元素应为 `chartSpace`。

    ??? info "Example"

        `Chart1.xml` 包含以下簇状条形图：

        ```xml
        <c:chartSpace …>
            <c:chart>
                <c:title>
                    …
                </c:title>
                <c:plotArea>
                    <c:layout>
                        …
                    </c:layout>
                    <c:barChart>
                        …
                    </c:barChart>
                </c:plotArea>
                <c:legend>
                    …
                </c:legend>
            </c:chart>
            …
        </c:chartSpace>
        ```
    

    对于 WordprocessingML 和 PresentationML 文档，图表的数据不直接存储在图表部件中。 
    相反，它应存储在该图表部件指定的嵌入式包 ([§15.2.11]) 部件所针对的嵌入式 SpreadsheetML 包 ([§12.2]) 中。 

    对于 SpreadsheetML 文档，图表的数据直接存储在绘图的父工作表中； 不得使用嵌入式 SpreadsheetML 包。
    
    图表部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal`）。
    
    图表部件允许与 ECMA-376 定义的以下部件有显式关系：
    
    * Chart Drawing ([§14.2.2])
    * Embedded Package ([§15.2.11])
    
    图表部件不应与 ECMA-376 定义的任何其他部件有任何隐式或显式关系。

=== "英文"

    **Chart Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.viewProps+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/chart`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/chart`</td>
        </tr>
    </table>

    An instance of this part type describes a chart.
    
    A package shall contain a Chart part for each chart in the document. In a WordprocessingML document, each such part shall be the target of an explicit relationship in a Main Document ([§11.3.10]) part. In a SpreadsheetML document, each such part shall be the target of an explicit relationship in a Drawings ([§12.3.8]) part. In a PresentationML document, each such part shall be the target of an explicit relationship in a Handout Master ([§13.3.3]), Notes Master ([§13.3.4]), Notes Slide ([§13.3.5]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part. This part is permitted to also be the target of an explicit relationship in a Chart Drawing ([§14.2.2]) part, if the chart that points at this Chart Drawing part is the target of a relationship from a Chartsheet part. In other words, the only time a chart can embed another chart is if the parent chart is part of a chartsheet

    ??? info "Example"

        The following Main Document part-relationship item contains relationships to two Chart parts, which are stored in the ZIP items `../charts/chartN.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/chart" Target="charts/chart1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/chart" Target="charts/chart2.xml"/>
        </Relationships>
        ```

        The following Drawings part-relationship item contains a relationship to a Chart part, which is stored in the ZIP item ../charts/chart1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/relationships/chart" Target="../charts/chart1.xml"/>
        </Relationships>
        ```

        The following Slide part-relationship item contains relationships to two Chart parts, which are stored in the ZIP items ../charts/chartN.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/chart" Target="../charts/chart1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/chart" Target="../charts/chart2.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be chartSpace.

    ??? info "Example"

        chart1.xml contains the following clustered bar chart:

        ```xml
        <c:chartSpace …>
            <c:chart>
                <c:title>
                    …
                </c:title>
                <c:plotArea>
                    <c:layout>
                        …
                    </c:layout>
                    <c:barChart>
                        …
                    </c:barChart>
                </c:plotArea>
                <c:legend>
                    …
                </c:legend>
            </c:chart>
            …
        </c:chartSpace>
        ```
    
    For WordprocessingML and PresentationML documents, the data for a chart is not stored in the Chart part directly. Instead, it shall be stored in an embedded SpreadsheetML package ([§12.2]) targeted by an Embedded Package ([§15.2.11]) part specified by that Chart part. For SpreadsheetML documents, the data for a chart is stored directly in the Drawing’s parent worksheet; no embedded SpreadsheetML package shall be used.
    
    A Chart part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Chart part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Chart Drawing ([§14.2.2])
    * Embedded Package ([§15.2.11])
    
    A Chart part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 14.2.2 图表绘制部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.chartshapes+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/chart`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/chartUserShapes`</td>
        </tr>
    </table>

    此零件类型的实例包含与此图表显式关联的所有基本绘图元素（形状）。 当移动图表时，这些绘图元素会自动随图表一起移动，并在调整图表大小时调整其大小。
    
    包允许每个图表部件包含一个图表绘图部件，并且每个此类部件应是图表 ([§14.2.1]) 部件的显式关系的目标。

    ??? info "Example"

        以下主文档部件关系项包含与两个图表部件的关系，这些部件存储在 ZIP 项 `../charts/chartN.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/chartUserShapes" Target="../drawings/drawing1.xml"/>
        </Relationships>
        ```

    此内容类型(content type)对应的部件的根元素应为 `userShapes`。

    ??? info "Example"

        ```xml
        <c:userShapes xmlns:cdr="…" xmlns:c="…">
            <cdr:relSizeAnchor>
                …
            </cdr:relSizeAnchor>
        </c:userShapes>
        ```
    
    图表绘制部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal）。
    
    图表绘制部件允许与 ECMA-376 定义的以下部件有明确的关系：
    
    * Chart ([§14.2.1])
    
    图表绘制部件不应与 ECMA-376 定义的任何其他部件有任何隐式或显式关系。

=== "英文"

    **Chart Drawing Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.chartshapes+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/chart`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/chartUserShapes`</td>
        </tr>
    </table>

    An instance of this part type contains all basic drawing elements (shapes) which are explicitly associated with this chart. These drawing elements are automatically moved with the chart when it is moved and resized when the chart is resized.
    
    A package is permitted to contain one Chart Drawing part per chart part, and each such part shall be the target of an explicit relationship from a Chart ([§14.2.1]) part.

    ??? info "Example"

        The following Main Document part-relationship item contains relationships to two Chart parts, which are stored in the ZIP items `../charts/chartN.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/chartUserShapes" Target="../drawings/drawing1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be userShapes.

    ??? info "Example"

        ```xml
        <c:userShapes xmlns:cdr="…" xmlns:c="…">
            <cdr:relSizeAnchor>
                …
            </cdr:relSizeAnchor>
        </c:userShapes>
        ```
    
    A Chart Drawing part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Chart Drawing part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Chart ([§14.2.1])
    
    A Chart Drawing part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 14.2.3 绘制颜色部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramColors+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramColors`</td>
        </tr>
    </table>

    此部件类型的实例包含图表的颜色信息。
    
    包中每个图表应包含一个图表颜色部件。 每个**图表颜色部件**(Diagram Colors part)应是 
    
    - WordprocessingML Main Document ([§11.3.10])
    - SpreadsheetML Drawings ([§12.3.8]) 
    - PresentationML Slide ([§13.3.8]) 
    
    这些部件的显式关系的目标。

    ??? info "Example"

        以下 SpreadsheetML 绘图部件关系项包含与两个图表颜色部件的关系，这两个部件存储在 ZIP 项 `../graphics/colorsN.xml` 中。

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/diagramColors" Target="../graphics/colors1.xml"/>
            <Relationship Id="rId8"
                Type="http://…/diagramColors" Target="../graphics/colors2.xml"/>
        </Relationships>
        ```

    该内容类型的一部件的根元素应为 `colorsDef` 。

    ??? info "Example"

        `color1.xml` 包含以下内容：

        ```xml
        <cs:colorsDef xmlns:cs="…" uniqueId="…" minVer="12.0">
            <cs:title lang="" val="Primary Accent 2"/>
            <cs:desc lang="" val="Primary Accent 2"/>
            <cs:catLst>
                <cs:cat type="accent1" pri="11200"/>
            </cs:catLst>
            <cs:styleLbl …>
                …
            </cs:styleLbl>
                …
            <cs:styleLbl …>
                …
            </cs:styleLbl>
        </cs:colorsDef>
        ```

    图颜色部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal）。
    
    图颜色部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Diagram Colors Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramColors+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramColors`</td>
        </tr>
    </table>

    An instance of this part type contains color information for a diagram.
    
    A package shall contain exactly one Diagram Colors part per diagram. Each Diagram Colors part shall be the target of an explicit relationship in a WordprocessingML Main Document ([§11.3.10]), SpreadsheetML Drawings ([§12.3.8]), or PresentationML Slide ([§13.3.8]) part.

    ??? info "Example"

        The following SpreadsheetML Drawings part-relationship item contains a relationship to two Diagram Colors parts, which are stored in the ZIP items `../graphics/colorsN.xml`.

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/diagramColors" Target="../graphics/colors1.xml"/>
            <Relationship Id="rId8"
                Type="http://…/diagramColors" Target="../graphics/colors2.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be colorsDef.

    ??? info "Example"

        colors1.xml contains the following:

        ```xml
        <cs:colorsDef xmlns:cs="…" uniqueId="…" minVer="12.0">
            <cs:title lang="" val="Primary Accent 2"/>
            <cs:desc lang="" val="Primary Accent 2"/>
            <cs:catLst>
                <cs:cat type="accent1" pri="11200"/>
            </cs:catLst>
            <cs:styleLbl …>
                …
            </cs:styleLbl>
                …
            <cs:styleLbl …>
                …
            </cs:styleLbl>
        </cs:colorsDef>
        ```

    A Diagram Colors part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Diagram Colors part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 14.2.4 绘制数据部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramData+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramData`</td>
        </tr>
    </table>

    此部件类型的实例包含图表的语义数据。

    包中每个**图表**(diagram)应包含一个**图表数据部件**(Diagram Data part)。 每个图表数据部件应是 
    
    - WordprocessingML:

        - Main Document ([§11.3.10]) 

    - SpreadsheetML:

        - Drawings part [§12.3.8]）； 

    - PresentationML:

        - Handout Master ([§13.3.3])
        - Notes Master ([§13.3.4])
        - Notes Slide ([§13.3.5])
        - Slide ([§13.3.8])
        - Slide Layout ([ §13.3.9])
        - Slide Master [§13.3.10]）

    等等这些部件显式关系的目标；

    ??? info "Example"

        以下 SpreadsheetML 绘图部件关系项包含与两个图表数据部件的关系，这两个部件存储在 ZIP 项 `../graphics/dataN.xml` 中。

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/diagramData" Target="../graphics/data1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/diagramData" Target="../graphics/data2.xml"/>
        </Relationships>
        ```

    该内容类型的一部件的根元素应为 `dataModel` 。

    ??? info "Example"

        `data1.xml` 包含以下内容：

        ```xml
        <dm:dataModel xmlns:dm="…">
            <dm:ptLst>
                …
            </dm:ptLst>
            <dm:cxnLst>
                …
            </dm:cxnLst>
            <dm:bg/>
            <dm:whole/>
        </dm:dataModel>
        ```

    图数据部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal ）。
    
    图表数据部件允许与 ECMA-376 定义的以下部件具有显式关系：
    
    * Image ([§15.2.14])
    
    图数据部件不应与 ECMA-376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Diagram Data Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramData+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramData`</td>
        </tr>
    </table>

    An instance of this part type contains the semantic data for a diagram.

    A package shall contain exactly one Diagram Data part per diagram. Each Diagram Data part shall be the target of an explicit relationship in a WordprocessingML Main Document ([§11.3.10]); a SpreadsheetML Drawings part ([§12.3.8]); or a PresentationML Handout Master ([§13.3.3]), Notes Master ([§13.3.4]), Notes Slide ([§13.3.5]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part.

    ??? info "Example"

        The following SpreadsheetML Drawings part-relationship item contains a relationship to two Diagram Data parts, which are stored in the ZIP items ../graphics/dataN.xml.

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/diagramData" Target="../graphics/data1.xml"/>
            <Relationship Id="rId5"
                Type="http://…/diagramData" Target="../graphics/data2.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be dataModel.

    ??? info "Example"

        data1.xml contains the following:

        ```xml
        <dm:dataModel xmlns:dm="…">
            <dm:ptLst>
                …
            </dm:ptLst>
            <dm:cxnLst>
                …
            </dm:cxnLst>
            <dm:bg/>
            <dm:whole/>
        </dm:dataModel>
        ```

    A Diagram Data part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Diagram Data part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Image ([§15.2.14])
    
    A Diagram Data part shall not have any implicit or explicit relationships to other parts defined by ECMA-376.

### 14.2.5 绘制布局定义部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramLayout+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramLayout`</td>
        </tr>
    </table>

    此部件类型的一个实例是一个模板，用于描述如何将与图表相关的数据映射到形状。
    
    包中的每个图表应包含一个**图表布局定义部件**(Diagram Layout Definition)。 
    每个**布局定义部件**( Layout Definition part)应是
    
    - WordprocessingML:

        - Main Document([§11.3.10])
    
    - SpreadsheetML:
      
      - Drawings part([§12.3.8])； 
    
    - PresentationML:
    
      - Handout Master ([§13.3.3])
      - Notes Master (§13.3.4)
      - Notes Slide ([§13.3.5])
      - Slide ([§13.3.8])
      - Slide Layout ([§13.3.9]) 
      - Slide Master ([§13.3.10])

    等等这些部件显式关系的目标。

    如果文档包含多个具有相同图形布局定义的图表，则每个图表都应具有其自己的该图表布局定义部件的副本。

    ??? info "Example"

        以下 SpreadsheetML 绘图部件关系项包含与两个图表布局定义部件的关系，这些部件存储在 ZIP 项 `../graphics/layoutN.xml` 中。

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/diagramLayout" Target="../graphics/layout1.xml"/>
            <Relationship Id="rId6"
                Type="http://…/diagramLayout" Target="../graphics/layout2.xml"/>
        </Relationships>
        ```

    该内容类型的一部件的根元素应为 `layoutDef` 。

    ??? info "Example"

        `layout1.xml` 包含以下内容：:

        ```xml
        <lo:layoutDef xmlns:lo="…" uniqueId="…2" minVer="12.0" defStyle="">
            <lo:title lang="" val="Hierarchy 2"/>
            <lo:desc lang="" val=""/>
            <lo:catLst>
                <lo:cat type="hierarchy" pri="2000"/>
            </lo:catLst>
            <lo:sampData>
                …
            </lo:sampData>
            <lo:styleData>
                …
            </lo:styleData>
            <lo:clrData>
                …
            </lo:clrData>
            <lo:layoutNode name="Name0" styleLbl="" moveWith="">
                …
            </lo:layoutNode>
        </lo:layoutDef>
        ```

    图布局定义部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal ）。
    
    图表布局定义部件允许与 ECMA-376 定义的以下部件和项目有明确的关系：

    * Image ([§15.2.14])
    
    图布局定义部件不应与 ECMA-376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Diagram Layout Definition Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramLayout+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramLayout`</td>
        </tr>
    </table>

    An instance of this part type is a template that describes how diagram-related data is mapped to a shape.
    
    A package shall contain exactly one Diagram Layout Definition part per diagram. Each Layout Definition part
    shall be the target of an explicit relationship from a WordprocessingML Main Document ([§11.3.10]); a
    SpreadsheetML Drawings part ([§12.3.8]); or a PresentationML Handout Master ([§13.3.3]), Notes Master (§13.3.4),
    Notes Slide ([§13.3.5]), Slide ([§13.3.8]), Slide Layout (§13.3.9), or Slide Master ([§13.3.10]) part. If a document
    contains multiple diagrams having the same graphic layout definition, each of those diagrams shall have its own
    copy of that Diagram Layout Definition part.

    ??? info "Example"

        The following SpreadsheetML Drawings part-relationship item contains a relationship to two Diagram Layout Definition parts, which are stored in the ZIP items ../graphics/layoutN.xml.

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/diagramLayout" Target="../graphics/layout1.xml"/>
            <Relationship Id="rId6"
                Type="http://…/diagramLayout" Target="../graphics/layout2.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be layoutDef.

    ??? info "Example"

        layout1.xml contains the following:

        ```xml
        <lo:layoutDef xmlns:lo="…" uniqueId="…2" minVer="12.0" defStyle="">
            <lo:title lang="" val="Hierarchy 2"/>
            <lo:desc lang="" val=""/>
            <lo:catLst>
                <lo:cat type="hierarchy" pri="2000"/>
            </lo:catLst>
            <lo:sampData>
                …
            </lo:sampData>
            <lo:styleData>
                …
            </lo:styleData>
            <lo:clrData>
                …
            </lo:clrData>
            <lo:layoutNode name="Name0" styleLbl="" moveWith="">
                …
            </lo:layoutNode>
        </lo:layoutDef>
        ```

    A Diagram Layout Definition part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Diagram Layout Definition part is permitted to have explicit relationships to the following parts and items defined by ECMA-376:

    * Image ([§15.2.14])
    
    A Diagram Layout Definition part shall not have any implicit or explicit relationships to other parts defined by ECMA-376.

### 14.2.6 绘制样式部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramStyle+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramQuickStyle`</td>
        </tr>
    </table>

    此部件类型的实例将图表语义信息映射到文档的主题。
    
    包中每个图表(diagram)应包含一个**图表样式部件**(Diagram Style part)。 每个**样式部件**(Style part)应是
    
    - WordprocessingML:

        - Main Document([§11.3.10])
    
    - SpreadsheetML:
      
      - Drawings part([§12.3.8])； 
    
    - PresentationML:
    
      - Handout Master ([§13.3.3])
      - Notes Master (§13.3.4)
      - Notes Slide ([§13.3.5])
      - Slide ([§13.3.8])
      - Slide Layout ([§13.3.9]) 
      - Slide Master ([§13.3.10])

    等等这些部件显式关系的目标。

    ??? info "Example"

        以下 SpreadsheetML 绘图部件关系项包含与两个图表样式部件的关系，这两个部件存储在 ZIP 项 `../graphics/quickStyleN.xml` 中。

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/diagramQuickStyle"
                Target="../graphics/quickStyle1.xml"/>
            <Relationship Id="rId7"
                Type="http://…/diagramQuickStyle"
                Target="../graphics/quickStyle2.xml"/>
            </Relationships>
        ```
    
    该内容类型的一部件的根元素应为 `styleDef` 。

    ??? info "Example"

        quickStyle1.xml contains the following:

        ```xml
        <qs:styleDef xmlns:qs="…" uniqueId="…" minVer="12.0">
            <qs:title lang="" val="Style 2"/>
            <qs:desc lang="" val="Style 2"/>
            <qs:catLst>
                <qs:cat type="simple" pri="10200"/>
            </qs:catLst>
            <qs:scene3d>
                …
            </qs:scene3d>
            <qs:style>
                …
            </qs:style>
            <qs:styleLbl name="…">
                …
            </qs:styleLbl>
                …
            <qs:styleLbl name="…">
                …
            </qs:styleLbl>
        </qs:styleDef>
        ```

    图样式部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal）。

    图样式部件不应与 ECMA-376 定义的其他部件有隐式或显式关系。

=== "英文"

    **Diagrame Style Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.drawingml.diagramStyle+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/diagram`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/diagramQuickStyle`</td>
        </tr>
    </table>

    An instance of this part type maps diagram semantic information to a document's theme.
    
    A package shall contain exactly one Diagram Style part per diagram. Each Style part shall be the target of an explicit relationship from a WordprocessingML Main Document ([§11.3.10]); a SpreadsheetML Drawings part ([§12.3.8]); or a PresentationML Handout Master ([§13.3.3]), Notes Master ([§13.3.4]), Notes Slide ([§13.3.5]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part.

    ??? info "Example"

        The following SpreadsheetML Drawings part-relationship item contains a relationship to two Diagram Style parts, which are stored in the ZIP items ../graphics/quickStyleN.xml.

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/diagramQuickStyle"
                Target="../graphics/quickStyle1.xml"/>
            <Relationship Id="rId7"
                Type="http://…/diagramQuickStyle"
                Target="../graphics/quickStyle2.xml"/>
            </Relationships>
        ```
    
    The root element for a part of this content type shall be styleDef.

    ??? info "Example"

        quickStyle1.xml contains the following:

        ```xml
        <qs:styleDef xmlns:qs="…" uniqueId="…" minVer="12.0">
            <qs:title lang="" val="Style 2"/>
            <qs:desc lang="" val="Style 2"/>
            <qs:catLst>
                <qs:cat type="simple" pri="10200"/>
            </qs:catLst>
            <qs:scene3d>
                …
            </qs:scene3d>
            <qs:style>
                …
            </qs:style>
            <qs:styleLbl name="…">
                …
            </qs:styleLbl>
                …
            <qs:styleLbl name="…">
                …
            </qs:styleLbl>
        </qs:styleDef>
        ```

    A Diagram Style part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Diagram Style part shall not have implicit or explicit relationships to other parts defined by ECMA-376. 

### 14.2.7 主题部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.theme+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/theme`</td>
        </tr>
    </table>

    此部件类型的实例包含有关文档主题的信息，该主题是**配色方案**(color scheme)、**字体方案**(font scheme)和 (format scheme)（后者也称为效果(effects)）的组合。
    
    对于 WordprocessingML 文档，主题的选择会影响标题的颜色和样式等。 
    
    对于 SpreadsheetML 文档，主题的选择会影响单元格内容和图表的颜色和样式等。 
    
    对于 PresentationML 文档，主题的选择会通过关联的母版影响幻灯片(slides)、讲义(handouts)和笔记(notes)的格式等。
    
    WordprocessingML 或 SpreadsheetML 包应包含零个或一个主题部件(Theme part)，该部件应是主文档(Main Document) ([§11.3.10]) 或工作簿(Workbook) ([§12.3.23]) 部件中隐式关系的目标。 

    PresentationML 包 中的**每个**
    
    - Handout Master ([§13.3.3])、
    - Notes Master ([§13.3.4])、
    - Slide Master ([§13.3.10])、
    - Presentation ([§13.3.6]) 
    
    应通过隐式关系包含零个或一个主题部件。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    ??? info "Example"

        以下 WordprocessingML 主文档部件关系项包含与主题部件的关系，该主题存储在 ZIP 项 `theme/theme1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/theme" Target="theme/theme1.xml"/>
        </Relationships>
        ```

    此内容类型的一部件的根元素应为`theme`。

    ??? info "Example"

        theme1.xml 包含以下内容，其中 clrScheme 、fontScheme 和 fmtScheme 元素的名称属性分别对应于文档的颜色方案、字体方案和格式方案：

        ```xml
        <a:theme xmlns:a="…">
            <a:themeElements>
                <a:clrScheme name="…">
                …
                </a:clrScheme>
                <a:fontScheme name="…">
                …
                </a:fontScheme>
                <a:fmtScheme name="…">
                …
                </a:fmtScheme>
            </a:themeElements>
            <a:objectDefaults/>
        </a:theme>
        ```

    主题部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal` ）。

    主题部件允许包含与 ECMA-376 定义的以下部件的显式关系：
    
    * Image ([§15.2.14])
    
    主题部件不应与 ECMA-376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Theme Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>`application/vnd.openxmlformats-officedocument.theme+xml`
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/theme`</td>
        </tr>
    </table>

    An instance of this part type contains information about a document's theme, which is a combination of color scheme, font scheme, and format scheme (the latter also being referred to as effects). For a WordprocessingML document, th choice of theme affects the color and style of headings, among other things. For a SpreadsheetML document, the choice of theme affects the color and style of cell contents and charts, among other things. For a PresentationML document, the choice of theme affects the formatting of slides, handouts, and notes via the associated master, among other things.
    
    A WordprocessingML or SpreadsheetML package shall contain zero or one Theme part, which shall be the target
    of an implicit relationship in a Main Document (§11.3.10) or Workbook ([§12.3.23]) part. A PresentationML
    package shall contain zero or one Theme part per Handout Master ([§13.3.3]), Notes Master ([§13.3.4]), Slide
    Master ([§13.3.10]) or Presentation (§13.3.6) part via an implicit relationship.

    ??? info "Example"

        The following WordprocessingML Main Document part-relationship item contains a relationship to the Theme part, which is stored in the ZIP item theme/theme1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/theme" Target="theme/theme1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be theme.

    ??? info "Example"

        theme1.xml contains the following, where the name attributes of the clrScheme, fontScheme, and fmtScheme elements correspond to the document's color scheme, font scheme, and format scheme, respectively:

        ```xml
        <a:theme xmlns:a="…">
            <a:themeElements>
                <a:clrScheme name="…">
                …
                </a:clrScheme>
                <a:fontScheme name="…">
                …
                </a:fontScheme>
                <a:fmtScheme name="…">
                …
                </a:fmtScheme>
            </a:themeElements>
            <a:objectDefaults/>
        </a:theme>
        ```

    A Theme part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Theme part is permitted to contain explicit relationships to the following parts defined by ECMA-376:
    
    * Image ([§15.2.14])
    
    A Theme part shall not have any implicit or explicit relationships to other parts defined by ECMA-376.

### 14.2.8 主题覆盖部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.themeOverride+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/themeOverride`</td>
        </tr>
    </table>

    此部件类型的实例包含有关对象**主题覆盖**(theme override)的信息，这些信息覆盖特定的
    
    - 幻灯片(slide)、
    - 笔记幻灯片(notes slide)
    - 讲义(handout)
 
    的**配色方案**(color scheme)、**字体方案**(font scheme)和**格式方案**(format scheme)（后者也称为效果(effects)）。
    
    PresentationML 包应通过隐式关系为每个 
    
    - Notes Slide ([§13.3.5])、
    - Slide ([§13.3.8]) 
    - Slide Layout ([§13.3.9]) 

    等等这些部件包含**零个或一个主题覆盖部件**(Theme Override part)。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    ??? info "Example"

        以下 WordprocessingML 主文档部件关系项包含与主题部件的关系，该主题存储在 ZIP 项 `theme/theme1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/themeOverride" Target="theme/themeoverride1.xml"/>
        </Relationships>
        ```

    该内容类型的一部件的根元素应为 `ossOverride` 。

    ??? info "Example"

        ```xml
        <a:ossOverride xmlns:a="…" >
            …
        </a:ossOverride>
        ```

    主题覆盖部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal` ）。

    主题覆盖部件不应包含与 ECMA-376 定义的其他部件的隐式或显式关系。

=== "英文"

    **Theme Override Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.themeOverride+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/themeOverride`</td>
        </tr>
    </table>

    An instance of this part type contains information about an object’s theme override, which are overrides to the color scheme, font scheme, and format scheme (the latter also being referred to as effects) for a particular slide, notes slide, or handout.
    
    A PresentationML package shall contain zero or one Theme Override part per Notes Slide ([§13.3.5]), Slide ([§13.3.8]), or Slide Layout ([§13.3.9]) part via an implicit relationship.

    ??? info "Example"

        The following WordprocessingML Main Document part-relationship item contains a relationship to the Theme part, which is stored in the ZIP item theme/theme1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/themeOverride" Target="theme/themeoverride1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be ossOverride.

    ??? info "Example"

        ```xml
        <a:ossOverride xmlns:a="…" >
            …
        </a:ossOverride>
        ```

    A Theme Override part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Theme Override part shall not contain implicit or explicit relationships to other parts defined by ECMA-376.

### 14.2.9 表格样式部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.presentationml.tableStyles+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/tableStyles`</td>
        </tr>
    </table>

    此部件类型的实例包含有关此演示文稿中的表格所使用的**表格样式**(table styles)的信息。 表格样式定义**行和列颜色**、**标题行颜色和文本**等特征。
    
    通过**隐式关系**，PresentationML 包中的每个**演示文稿部件**(Presentation part) ([§13.3.6]) **不得包含超过一个表格样式部件**。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](./chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    ??? info "Example"

        tablestyles.xml contains the following:

        ```xml
        <a:tblStyleLst xmlns:a="…">
            <a:tblStyle>
                …
            </a:tblStyle>
        </a:tblStyleLst>
        ```

    表样式部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal）。
    
    表样式部件不应包含与 ECMA-376 定义的其他部件的隐式或显式关系。

=== "英文"

    **Table Styles Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.presentationml.tableStyles+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>`http://purl.oclc.org/ooxml/drawingml/main`</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/tableStyles`</td>
        </tr>
    </table>

    An instance of this part type contains information about the table styles used by tables in this presentation. A table style defines characteristics such as row and column colors, heading row colors, and text.
    
    A PresentationML package shall contain no more than one Table Styles part per Presentation ([§13.3.6]) part via an implicit relationship.

    ??? info "Example"

        tablestyles.xml contains the following:

        ```xml
        <a:tblStyleLst xmlns:a="…">
            <a:tblStyle>
                …
            </a:tblStyle>
        </a:tblStyleLst>
        ```

    A Table Styles part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Table Styles part shall not contain implicit or explicit relationships to other parts defined by ECMA-376.

<!--链接定义-->
[§13.3.1]: ./chapter-13.md#1331-评论作者部件
[§13.3.2]: ./chapter-13.md#1332-评论部件
[§13.3.3]: ./chapter-13.md#1333-讲义母板部件
[§13.3.4]: ./chapter-13.md#1334-笔记母版部件
[§13.3.5]: ./chapter-13.md#1335-笔记幻灯片部件
[§13.3.6]: ./chapter-13.md#1336-演示部件
[§13.3.7]: ./chapter-13.md#1337-演示属性部件
[§13.3.8]: ./chapter-13.md#1338-幻灯片部件
[§13.3.9]: ./chapter-13.md#1339-幻灯片布局部件
[§13.3.10]: ./chapter-13.md#13310-幻灯片母版部件
[§13.3.11]: ./chapter-13.md#13311-幻灯片同步数据部件
[§13.3.12]: ./chapter-13.md#13312--用户已定义标签部件
[§13.3.13]: ./chapter-13.md#13313-视图属性部件

[§14]: #14-drawingml
[§14.1]: #141-drawingml-特定术语词汇表
[§14.2]: #142-部件概览
[§14.2.1]: #1421-图表部件
[§14.2.2]: #1422-图表绘制部件
[§14.2.3]: #1423-绘制颜色部件
[§14.2.4]: #1424-绘制数据部件
[§14.2.5]: #1425-绘制布局定义部件
[§14.2.6]: #1426-绘制样式部件
[§14.2.7]: #1427-主题部件
[§14.2.8]: #1428-主题覆盖部件
[§14.2.9]: #1429-表格样式部件

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
