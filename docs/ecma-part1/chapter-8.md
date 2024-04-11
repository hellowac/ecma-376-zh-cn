# 8. 概述

=== "中文"

    **这章为信息性的内容**

    本节包含 Office Open XML 的概述。

=== "英文"

    **Overview**

    **This clause is informative.**

    This clause contains an overview of Office Open XML.

## 8.1 内容概览

=== "中文"

    该标准主要包含以下三类信息：

    1. 规范性 W3C XML 模式、信息丰富的 RELAX NG 模式以及用于根据这些模式验证文档语法的相关验证程序（[附录 A] 和[附录 B]）
    2. XML 元素语义的描述。 XML 元素的语义是指人类对其的预期解释（主要在 [§11]、[§12]、[§13] 和 [§14] 中）.
    3. 书面形式的附加语法约束

=== "英文"

    **Content Overview**

    This standard contains predominantly the following three types of information:

    1. Normative W3C XML Schemas, informative RELAX NG schemas and an associated validation procedure for validating document syntax against those schemas (Annex A and Annex B)
    2. Descriptions of XML element semantics. The semantics of an XML element refers to its intended interpretation by a human being (chiefly in [§11], [§12], [§13], and [§14])
    3. Additional syntax constraints in written form

## 8.2 包和部件

=== "中文"

    Office Open XML 文档表示为存储在称为包的容器中的一系列相关部件。 有关包及其部件之间关系的信息存储在包的包关系 ZIP 项中。 有关两个部件之间关系的信息存储在源部件的部件关系 ZIP 项中。 包是一个普通的 ZIP 存档，其中包含该包的内容类型项、关系项和部件(Part)。 （ECMA-376-2 中进一步讨论了包。）

    WordprocessingML 文档包含文本正文的一部件； 它还可能包含该文本引用的图像的一部件，以及定义文档特征、样式和字体的部件。 SpreadsheetML 文档包含每个工作表的单独部件； 它还可能包含图像部件。 PresentationML 文档包含每张幻灯片的单独部件。

=== "英文"

    **Packages and Parts**

    An Office Open XML document is represented as a series of related parts that are stored in a container called a package. Information about the relationships between a package and its parts is stored in the package's package-relationship ZIP item. Information about the relationships between two parts is stored in the partrelationship ZI item for the source part. A package is an ordinary ZIP archive, which contains that package's content-type item, relationship items, and parts. (Packages are discussed further in ECMA-376-2.)
    
    A WordprocessingML document contains a part for the body of the text; it might also contain a part for an image referenced by that text, and parts defining document characteristics, styles, and fonts. A SpreadsheetML document contains a separate part for each worksheet; it might also contain parts for images. A PresentationML document contains a separate part for each slide.

## 8.3 消费者和生产者

=== "中文"

    能够读取和理解包的工具称为*消费者*，而能够创建包的工具称为*生产者*。 应用程序可以是消费者、生产者或两者兼而有之。 例如，当文字处理器创建新文档时，它充当生产者。 当它用于打开现有文档以进行阅读或搜索时，它充当消费者。 当它用于打开现有文档、编辑它并保存结果时，它既充当消费者又充当生产者。 电子表格和演示应用程序也存在类似的情况。

=== "英文"

    **Consumers and Producers**

    A tool that can read and understand a package is called a *consumer*, while one that can create a package is called a producer. An application can be a consumer, a producer, or both. For example, when a word processor creates a new document, it acts as a producer. When it is used to open an existing document for reading or search purposes, it acts as a consumer. When it is used to open an existing document, edit it, and save the result, it acts as both consumer and producer. Similar scenarios exist for spreadsheet and presentation applications.

## 8.4 WordprocessingML

=== "中文"

    本节介绍了 WordprocessingML 包的整体形式，并标识了它的一些主要组件。 （更详细的介绍见[附录L]。）

    WordprocessingML 包具有 officeDocument 类型的关系，该关系指定包中主要部件的位置。 对于 WordprocessingML 文档，该部件包含文档的主要文本。

    WordprocessingML 包的主要部件以文字处理根元素开始。 该元素包含一个正文，而正文又包含一个或多个段落（以及表格、图片等）。 段落包含一个或多个连续，其中连续是具有相同属性集的一个或多个文本片段的容器。 与定义文字处理文档的逻辑部件的许多元素一样，每个运行和段落都可以具有与其关联的一组属性。 例如，运行可能具有粗体属性，这表示运行的文本将以粗体字体显示。
    
    WordprocessingML 文档被组织为多个部件，并且部件中出现文本的页面布局由该部件的属性控制。 例如，每个部件可以有自己的页眉和页脚。
    
    文档部件的一种关系指定文档的样式。 样式定义文本显示格式。 样式可以具有可应用于各个段落或运行的属性。 样式通过减少重复定义和属性的数量以及更改文档外观所需的工作量，使运行更加紧凑。 通过样式，共享同一样式的所有文本片段的外观都可以在该样式的定义中的一个位置进行更改。
    
    可以通过编号定义实例或编号样式对一系列段落应用编号。
    
    WordprocessingML 文档中的数据可以组织在表格中，表格是组织成*行*和*列*的二维单元格网格。 单元格和整个表格可以具有关联的属性。 例如，单元格可以包含文本和段落。
    
    WordprocessingML 文档中的文本可以通过使用字段动态确定。 字段由字段指令（指示字段动态行为的文本）和字段结果（字段指令动态计算得出的文本）组成。例如，页码表示为字段。超链接由两条信息组成：超链接本身（用户单击的文本）以及链接的目标。潜在目标包括外部文件、电子邮件地址、网站和文档本身内的书签。
    
    WordprocessingML 文档还可以包含应用于任意文档内容的自定义标记、用户定义语义。
    
    WordprocessingML 文档不是作为一个整体存储在单个部件中；而是存储在一个单独的部件中。 相反，实现某些功能分组的元素存储在单独的部件中。 例如，文档中的所有脚注都存储在一个脚注部件中，而每个部件最多可以有三个不同的页眉部件和三个不同的页脚部件，以支持奇数页、偶数页和第一页。

=== "英文"

    **WordprocessingML**

    This subclause introduces the overall form of a WordprocessingML package, and identifies some of its main components. (See Annex L for a more detailed introduction.)

    A WordprocessingML package has a relationship of type officeDocument, which specifies the location of the main part in the package. For a WordprocessingML document, that part contains the main text of the document.

    A WordprocessingML package’s main part starts with a word processing root element. That element contains a body, which, in turn, contains one or more paragraphs (as well as tables, pictures, and the like). A paragraph contains one or more runs, where a run is a container for one or more pieces of text having the same set of properties. Like many elements that defined a logical piece of a word processing document, each run and paragraph can have associated with it a set of properties. For example, a run might have the property bold, which indicates that run's text is to be displayed in a bold typeface.
    
    A WordprocessingML document is organized into sections, and the layout of a page on which the text appears within a section is controlled by that section's properties. For example, each section can have its own headers and footers.
    
    One relationship from the document part specifies the document’s styles. A style defines a text display format. A style can have properties, which can be applied to individual paragraphs or runs. Styles make runs more compact by reducing the number of repeated definitions and properties, and the amount of work required to make changes to the document's appearance. With styles, the appearance of all the pieces of text that share a common style can be changed in one place, in that style's definition.
    
    A series of paragraphs can have numbering applied to them via a numbering definition instance or a numbering style.
    
    Data in a WordprocessingML document can be organized in a table, a two-dimensional grid of cells organized into rows and columns. Cells and whole tables can have associated properties. A cell can contain text and paragraphs, for example.
    
    Text within a WordprocessingMLdocument can be determined dynamically via the use of fields. Fields consist of field instructions (the text that dictates the field's dynamic behavior) and the field result (the text resulting from the dynamic calculation of the field instructions. For example, page numbers are represented as fields. A hyperlink consists of two pieces of information: the hyperlink itself—the text the user clicks—and the target for the link. Potential targets include external files, e-mail addresses, web sites, and bookmarks within the document itself.
    
    A WordprocessingML document can also contain custom markup, user-defined semantics applied to arbitrary document content.
    
    A WordprocessingML document is not stored as one large body in a single part; instead, the elements that implement certain groupings of functionality are stored in separate parts. For example, all footnotes in a document are stored in one footnote part, while each section can have up to three different header parts and three different footer parts, to support headers and footers on odd-numbered pages, even-numbered pages, and the first page.

## 8.5 SpreadsheetML

=== "中文"

    本小节介绍了 SpreadsheetML 包的整体形式，并标识了它的一些主要组件。 （更详细的介绍见[附件L]。）
    
    SpreadsheetML 包具有 officeDocument 类型的关系，它指定包中主要部件的位置。 对于 SpreadsheetML 文档，该部件包含工作簿定义。
    
    SpreadsheetML 包的主要部件从电子表格根元素开始。 该元素是一个工作簿，它引用一个或多个工作表，而这些工作表又包含数据。 工作表是组织成行和列的二维单元格网格。
    
    单元是存储和操作数据的主要场所。 单元格可以具有多种特征，例如数字、文本、日期或时间格式； 结盟; 字体； 颜色; 和边界。 每个单元格都由单元格引用（其列标题和行标题的组合）来标识。
    
    工作表中的每个水平单元格集称为行，每行都有一个从 1 开始按顺序编号的标题。工作表中的每个垂直单元格集称为列，每列都有一个按字母顺序命名的标题，从 A 开始–Z，然后是 AA–AZ、BA–BZ，依此类推。
    
    单元格可以包含公式（而不是数据），该公式是计算值的方法。 一些公式（称为函数）是预定义的，而另一些则是用户定义的。 预定义公式的示例有 **AVERAGE**、**MAX**、**MIN** 和 **SUM**。 函数接受一个或多个对其进行运算的参数，并产生结果。 例如，在公式 **SUM(B1:B4)** 中，有一个参数 **B1:B4**，它是单元格范围 B1–B4（含）。
    
    SpreadsheetML 文档可以包含以下其他功能：注释、超链接、图像以及排序和筛选的表格。
    
    SpreadsheetML 文档不是作为一个整体存储在单个部件中； 相反，实现某些功能分组的元素存储在单独的部件中。 例如，工作表的所有数据都存储在该工作表的部件中，所有工作表中的所有字符串文字都存储在单个共享字符串部件中，并且每个具有注释的工作表都有自己的注释部件。

=== "英文"

    **SpreadsheetML**

    This subclause introduces the overall form of a SpreadsheetML package, and identifies some of its main components. (See Annex L for a more detailed introduction.)
    
    A SpreadsheetML package has a relationship of type officeDocument, which specifies the location of the main part in the package. For a SpreadsheetML document, that part contains the workbook definition.
    
    A SpreadsheetML package’s main part starts with a spreadsheet root element. That element is a workbook, which refers to one or more worksheets, which, in turn, contain the data. A worksheet is a two-dimensional grid of cells that are organized into rows and columns.
    
    The cell is the primary place in which data is stored and operated on. A cell can have a number of characteristics, such as numeric, text, date, or time formatting; alignment; font; color; and a border. Each cell is identified by a cell reference, a combination of its column and row headings.
    
    Each horizontal set of cells in a worksheet is called a row, and each row has a heading numbered sequentially, starting at 1. Each vertical set of cells in a worksheet is called a column, and each column has an alphabetic heading named sequentially from A–Z, then AA–AZ, BA–BZ, and so on.
    
    Instead of data, a cell can contain a formula, which is a recipe for calculating a value. Some formulas—called functions—are predefined, while others are user-defined. Examples of predefined formulas are AVERAGE, MAX, MIN, and SUM. A function takes one or more arguments on which it operates, producing a result. For example, in the formula SUM(B1:B4), there is one argument, B1:B4, which is the range of cells B1–B4, inclusive.
    
    Other features that a SpreadsheetML document can contain include the following: comments, hyperlinks, images, and sorted and filtered tables.
    
    A SpreadsheetML document is not stored as one large body in a single part; instead, the elements that implement certain groupings of functionality are stored in separate parts. For example, all the data for a worksheet is stored in that worksheet's part, all string literals from all worksheets are stored in a single shared string part, and each worksheet having comments has its own comments part.

## 8.6 PresentationML

=== "中文"

    本小节介绍了PresentationML包的整体形式，并标识了它的一些主要组件。 （更详细的介绍见[附件L]。）
    
    PresentationML 包具有 officeDocument 类型的关系，它指定包中主要部件的位置。 对于PresentationML 文档，该部件包含演示定义。
    
    {== PresentationML 包的主要部件以 演示根元素(presentation root element) 开始。 该元素包含一个**演示文稿(presentation)**，而演示文稿又引用**幻灯片列表(slide list)**、**幻灯片母版列表(slide master list)**、**注释母版列表(notes master list)**和**讲义母版列表(handout master list)**。 **幻灯片列表(slide list)**是指演示文稿中的所有幻灯片；** 幻灯片母版列表(slide master list)**是指演示文稿中使用的所有幻灯片母版； 笔记主文件(notes master)包含有关笔记页面格式的信息； **讲义母板(handout master)**描述了讲义的外观。 ==}

    讲义(handout)是一组打印过的幻灯片，可以分发给观众以供将来参考。
    
    除了文本和图形之外，每张幻灯片还可以包含**评论(comments)**和**注释(notes)**，可以具有**布局(layout)**，并且可以是一个或多个自定义演示文稿(custom persentations)的一部分。 （评论(comment)是供维护演示文稿幻灯片的人员使用的注解。注释(note)是供演示者或观众使用的提醒或文本。）
    
    PresentationML 文档可以包含以下其他功能：动画(animation)、音频、视频和幻灯片之间的过渡(transitions)。
    
    PresentationML 文档并不是作为一个整体存储在一个单独的部件中； 相反，实现某些功能分组的元素存储在单独的部件中。 例如，文档中的所有评论都存储在一个评论部件（comment part）中，而每张幻灯片都有自己的部件（Part）。

=== "英文"

    **PresentationML**

    This subclause introduces the overall form of a PresentationML package, and identifies some of its main components. (See Annex L for a more detailed introduction.)
    
    A PresentationML package has a relationship of type officeDocument, which specifies the location of the main part in the package. For a PresentationML document, that part contains the presentation definition.
    
    A PresentationML package’s main part starts with a presentation root element. That element contains a presentation, which, in turn, refers to a slide list, a slide master list, a notes master list, and a handout master list. The slide list refers to all of the slides in the presentation; the slide master list refers to all of the slide masters used in the presentation; the notes master contains information about the formatting of notes pages; and the handout master describes how a handout looks.

    A handout is a printed set of slides that can be handed out to an audience for future reference.
    
    As well as text and graphics, each slide can contain comments and notes, can have a layout, and can be part of one or more custom presentations. (A comment is an annotation intended for the person maintaining the presentation slide deck. A note is a reminder or piece of text intended for the presenter or the audience.)
    
    Other features that a PresentationML document can contain include the following: animation, audio, video, and transitions between slides.
    
    A PresentationML document is not stored as one large body in a single part; instead, the elements that implement certain groupings of functionality are stored in separate parts. For example, all comments in a document are stored in one comment part while each slide has its own part.

## 8.7 Supporting MLs

=== "中文"

    本小节介绍了跨包类别使用的标记语言集。 （更详细的介绍见[附录L]。）

    上面描述的三种标记语言定义了包的结构，包要么是**文档**（WordprocessingML），要么是**电子表格**（SpreadsheetML），要么是**演示文稿**（PresentationML）。 然而，**还有一组共享标记语言用于图表、图表和绘图对象等常见元素**。 下面讨论这些 ML。

=== "英文"

    **Supporting MLs**

    This subclause introduces the set of markup languages used across package categories. (See [Annex L] for a more detailed introduction.)

    The three markup languages described above define the structure of a package that is either a document (WordprocessingML), a spreadsheet (SpreadsheetML), or a presentation (PresentationML). However, there is also a set of shared markup languages used for common elements such as charts, diagrams, and drawing objects. These MLs are discussed below.

### 8.7.1 DrawingML

=== "中文"

    DrawingML 指定包中绘图元素的位置和外观。 例如，这些元素可以是但不限于形状、图片和表格。 DrawingML XML 片段的根元素指定文档中此位置是否存在绘图。
    
    形状是一个几何对象，例如圆形、正方形或矩形； 图片是文档内呈现的图像； 表格是组织成行和列的二维单元格网格。 单元格和整个表格可以具有关联的属性。 例如，单元格可以包含文本。
    
    DrawingML 还指定包中图表的位置和外观。 图表部件的根元素是图表，并指定图表在文档中此位置的外观。
    
    此外，DrawingML 指定包范围的外观特征，例如包的主题。 文档的**主题**指定**配色方案**、**字体**和**效果**，文档的各个部件（例如文本、绘图、图表和图表）可以引用这些主题，以创建一致的视觉表示。
    
    图表是以图形方式表示数据的形式，例如饼图、条形图、折线图，以便使数据中的趋势和异常更加直观。
    
    DrawingML 还指定文档中图表的位置和外观。 以下四个部件共同定义了一个图表：

    * **数据**部件(*data* part) ([§14.2.4]) 指定图表中呈现的各个信息项。 通常，每一段都是一行简单的文本，但根据图表的不同，数据项也可能是图像。
    * **布局**部件(*layout* part)（[§14.2.5]）指定如何布局数据和形状以创建结果图。
    * **颜色**部件(*colors* part) ([§14.2.3]) 指定应用于图中每个单独形状的颜色。
    * **样式**部件(*styles* part) ([§14.2.6]) 定义图表中的每个单独形状如何映射到文档的主题。

=== "英文"

    **DrawingML**

    DrawingML specifies the location and appearance of drawing elements in a package. For example, these elements could be, but are not limited to, shapes, pictures, and tables. The root element of a DrawingML XML fragment specifies the presence of a drawing at this location in the document.
    
    A shape is a geometric object such as a circle, square, or rectangle; a picture is an image presented inside the document; and a table is a two-dimensional grid of cells organized into rows and columns. Cells and whole tables can have associated properties. A cell can contain text, for example.
    
    DrawingML also specifies the location and appearance of charts in a package. The root element of a chart part is chart, and specifies the appearance of the chart at this location in the document.
    
    In addition, DrawingML specifies package-wide appearance characteristics, such as the package's theme. The theme of a document specifies the color scheme, fonts, and effects, which can be referenced by parts of the document—such as text, drawings, charts, and diagrams—in order to create a consistent visual presentation.
    
    A chart is a presentation of data in a graphical fashion, such as a pie chart, bar chart, line chart, in order to make trends and exceptions in the data more visually apparent.
    
    DrawingML also specifies the location and appearance of diagrams in a document. Together, the following four parts define a diagram:

    * The data part ([§14.2.4]) specifies individual items of information presented in the diagram. Typically, each piece is a simple line of text, but depending on the diagram, an item of data might also be an image.
    * The layout part ([§14.2.5]) specifies how the data and shapes are laid out to create the resulting diagram.
    * The colors part ([§14.2.3]) specifies the color which is applied to each individual shape in the diagram.
    * The styles part ([§14.2.6]) defines how each individual shape in the diagram maps to the document's theme.

### 8.7.2 自定义XML数据属性

=== "中文"

    自定义 XML 数据属性允许在包中存储任意 XML 以及该 XML 使用的架构（Schema）信息。

=== "英文"

    **Custom XML Data Properties**

    Custom XML Data properties allow the ability to store arbitrary XML in a package, along with schema information used by that XML.

### 8.7.3 文件属性

=== "中文"

    包的**核心文件属性**使用户能够从该包内发现、获取和设置常见的属性集，无论它是 WordprocessingML、SpreadsheetML 或PresentationML 包，还是 OPC 的其他用途。 此类属性包括创建者姓名、创建日期、标题和描述。
    
    **扩展文件属性**特定于 Office Open XML 包。 例如，对于 WordprocessingML 包，这些属性包括文档中的字符数、单词数、行数、段落数和页数。 对于 SpreadsheetML 包，这些属性包括工作表标题。 对于PresentationML 包，这些属性包括演示文稿格式、幻灯片数量、注释数量以及是否隐藏任何幻灯片。
    
    **自定义文件属性**由用户定义。 示例包括为其准备文档的客户的姓名、发生某些事件的日期/时间、文档编号或某些布尔状态标志。 每个自定义文件属性都有一个值，并且该值有一个数据类型。

=== "英文"

    **File Properties**

    The core file properties of a package enable users to discover, get, and set common sets of properties from within that package, regardless of whether it’s a WordprocessingML, SpreadsheetML, or PresentationML package, or another use of OPC. Such properties include creator name, creation date, title, and description.
    
    Extended file properties are specific to Office Open XML packages. For example, for a WordprocessingML package, these properties include the number of characters, words, lines, paragraphs, and pages in the document. For a SpreadsheetML package, these properties include worksheet titles. For a PresentationML package, these properties include presentation format, the number of slides, the number of notes, and whether or not any slides are hidden.
    
    Custom file properties are defined by the user. Examples include the name of the client for whom the document was prepared, a date/time on which some event happened, a document number, or some Boolean status flag. Each custom file property has a value, and that value has a data type. 

### 8.7.4 数学

=== "中文"

    数学主要在文档中用于指定方程的结构和外观。 最外面的根元素可以是 **oMath** 或 **oMathPara**，后者是包含一个或多个方程的数学段落，其中每个方程都使用单个 **oMath** 元素指定

=== "英文"

    **Math**

    Math is used, mainly in documents, to specify the structure and appearance of equations. The outermost root element can be either oMath or oMathPara, the latter being a math paragraph with one or more equations where each equation is specified using a single oMath element

### 8.7.5 参考书目

=== "中文"

    参考书目指定文档中存储的所有参考文献的结构，以用于引文或参考书目。

=== "英文"

    **Bibliography**

    Bibliography specifies the structure for all references stored within a document, for use in citations or a bibliography.
