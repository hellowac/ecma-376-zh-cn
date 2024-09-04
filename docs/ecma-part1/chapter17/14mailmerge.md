# 17.14 邮件合并

**Mail Merge**

=== "中文"

    邮件合并是指WordprocessingML文档与外部数据源的数据协同工作的操作，根据WordprocessingML中称为字段的一组代码，将这些数据导入到文档中。
    
    一个包含 mailMerge 元素（[§17.14.20]）并因此连接到外部数据源的 WordprocessingML 文档称为*源文档*(source document)。除了连接到外部数据源并包含字段之外，源文档还可以包含任何常规的 WordprocessingML 构造，例如：
    
    - 文本运行(Text runs)
    - 段落(Paragraphs)
    - 图像(Images)
    - 表格(Tables)
    - 编号(Numbering)
    - 等等
    
    存储在 WordprocessingML 文档中的邮件合并数据有两个关键部分：
    
    9.&nbsp;连接文档与外部数据源的信息
    10.&nbsp;使用外部数据填充文档中字段的信息
    
    一旦合并文档中的字段被外部数据填充，邮件合并就完成了，生成的文件称为*邮件合并文档(mail merged documents)*或简称为*合并文档(merged documents)*。 WordprocessingML 文档的邮件合并设置存储在两个位置：
    
    - 标准邮件合并设置存储为 mailMerge 元素（[§17.14.20]）的子元素
    - 一组存储在 odso 元素（[§17.14.25]）中的附加邮件合并设置，统称为 Office Data Source Object 设置。 Office Data Source Object 是与邮件合并一起存储的标准设置的扩展，它执行两个功能：首先，它提供有关邮件合并数据源的附加信息，具体而言：关于如何将数据源中的列映射到 MERGEFIELD 字段的信息以及在创建合并文档时应包括和排除的记录的信息。其次，它提供一个备用的连接信息集，应该在 dataType 元素（[§17.14.10]）指定为 native 的情况下使用。此备用连接字符串为选择支持 ODSO 连接字符串语法的应用程序提供了附加的连接信息。
    
    【示例：考虑一个包含静态 WordprocessingML 构造（如文本运行和段落）以及两个调用 Courtesy Title 和 Last Name 数据的 WordprocessingML MERGEFIELD 字段（[§17.16.5.35]）的 WordprocessingML 文档。每个字段的字段代码如下，由 `{}` 字符界定：
    
    ![Image title](./imgs/16img02.png)
    
    如果将以下 WordprocessingML 添加到此文档中，此文档将成为*源文档*(source document)，而不仅仅是一个标准的 WordprocessingML 文档，因为 mailMerge （§17.14.20）元素指定了连接到外部电子表格数据源所需的元素和属性。
    
    ```xml
    <w:mailMerge>
        …
        <w:dataType w:val="spreadsheet" />
        <w:query w:val="SELECT * FROM `Sheet1$`" />
        <w:dataSource r:id="rId1" />
        …
    </w:mailMerge>
    ```
    
    在这里，dataType（[§17.14.10]）和dataSource（[§17.14.9]）元素指定给定文档必须连接到由 dataSource 元素（[§17.14.9]）中的关系值 rId1 指定的外部数据源目标。在连接到外部数据源的同时，源文档与托管应用程序和/或数据源访问应用程序一起从外部数据源提取数据，以执行由 connectString（[§17.14.8]）和 query（[§17.14.26]）元素指定的合并操作。】

=== "英文"

    Mail merge refers to an operation by which WordprocessingML documents can work in conjunction with data from an external data source, importing this data into a document according to a set of codes contained in WordprocessingML known as fields.
    
    A WordprocessingML document that contains the mailMerge element ([§17.14.20]) and is therefore connected to an external data source, is known as a *source document*. In addition to being connected to an external data source and containing fields, a source document can contain any regular WordprocessingML constructs such as:
    
    - Text runs
    - Paragraphs
    - Images
    - Tables
    - Numbering
    - Etc.
    
    There are two key parts of the mail merge data stored in a WordprocessingML document
    
    
    9.&nbsp;Information connecting a document to an external data source
    
    10.&nbsp;Information populating fields within that document with external data.
    
    Once the fields in a merged document have been populated with external data, mail merge has been completed and the resulting files are known as mail merged documents or simply merged documents.
    The mail merge settings for a WordprocessingML document are stored in two locations:
    
    
    - The standard mail merge settings are stored as the child elements of the mailMerge element ([§17.14.20])
    = A set of additional mail merge settings stored in the odso element ([§17.14.25]), and collectively referred to as the Office Data Source Object settings. The Office Data Source Object is an extension to the standard settings stored with a mail merge which performs two functions: First, it provides additional information about the mail merge data source, specifically: information about how to map the columns in the data source to MERGEFIELD fields and information about records which shall be included and excluded when creating merged documents. Second, it provides an alternate set of connection information which should be used when the dataType element ([§17.14.10]) specifies a value of native. This alternate connection string provides additional connection information for applications which choose to support the ODSO connection string syntax.
    
    [Example: Consider a WordprocessingML document containing static WordprocessingML constructs such as text runs and paragraphs in addition to two WordprocessingML MERGEFIELD fields ([§17.16.5.35]) calling for Courtesy Title and Last Name data. The field codes for each field are displayed, delimited by {} characters:
    
    <figure markdown="span">
      ![Image title](./imgs/16img02.png)
    </figure>
    
    
    If the following WordprocessingML was added to this document, this document would become a source
    document rather than just a standard WordprocessingML document, as the mailMerge (§17.14.20) element specifies the elements and attributes necessary to enabled the document to connect to an external spreadsheet data source.
    
    ```xml
    <w:mailMerge>
        …
        <w:dataType w:val="spreadsheet" />
        <w:query w:val="SELECT * FROM `Sheet1$`" />
        <w:dataSource r:id="rId1" />
        …
    </w:mailMerge>
    ```
    
    Here, the dataType ([§17.14.10]) and dataSource ([§17.14.9]) elements specify that the given document must be connected to the external data source target by the relationship whose relationship value is rId1 as specified in the dataSource element ([§17.14.9]). While connected to the external data source, the source document together with the hosting application and/or data source access application extracts data from the external data source to perform the merge as specified by the connectString ([§17.14.8]) and query ([§17.14.26]) elements. end example]


## 17.14.1 active (记录包含在邮件合并中)

**active (Record Is Included in Mail Merge)**

=== "中文"

=== "英文"

## 17.14.2 activeRecord (合并文档中当前显示的记录)

**activeRecord (Record Currently Displayed In Merged Document)**

=== "中文"

=== "英文"

## 17.14.3 addressFieldName (包含电子邮件地址的列)

**addressFieldName (Column Containing E-mail Address)**

=== "中文"

=== "英文"

## 17.14.4 checkErrors (邮件合并错误报告设置)

**checkErrors (Mail Merge Error Reporting Setting)**

=== "中文"

=== "英文"

## 17.14.5 colDelim (数据源的列分隔符)

**colDelim (Column Delimiter for Data Source)**

=== "中文"

=== "英文"

## 17.14.6 column (正在映射的列的索引)

**column (Index of Column Being Mapped)**

=== "中文"

=== "英文"

## 17.14.7 column (包含记录的唯一值的列的索引)

**column (Index of Column Containing Unique Values for Record)**

=== "中文"

=== "英文"

## 17.14.8 connectString (数据源连接字符串)

**connectString (Data Source Connection String)**

=== "中文"

=== "英文"

## 17.14.9 dataSource (数据源文件路径)

**dataSource (Data Source File Path)**

=== "中文"

=== "英文"

## 17.14.10 dataType (数据源类型)

**dataType (Data Source Type)**

=== "中文"

=== "英文"

## 17.14.11 destination (合并文档目标)

**destination (Merged Document Destination)**

=== "中文"

=== "英文"

## 17.14.12 doNotSuppressBlankLines (从合并文档中删除空行)

**doNotSuppressBlankLines (Remove Blank Lines from Merged Documents)**

=== "中文"

=== "英文"

## 17.14.13 dynamicAddress (使用基于国家/地区的地址字段排序)

**dynamicAddress (Use Country-Based Address Field Ordering)**

=== "中文"

=== "英文"

## 17.14.14 fHdr (数据源的第一行包含列名称)

**fHdr (First Row of Data Source Contains Column Names)**

=== "中文"

=== "英文"

## 17.14.15 fieldMapData (用于合并字段映射的外部数据源)

**fieldMapData (External Data Source to Merge Field Mapping)**

=== "中文"

=== "英文"

## 17.14.16 headerSource (标头定义文件路径)

**headerSource (Header Definition File Path)**

=== "中文"

=== "英文"

## 17.14.17 lid (合并字段名称语言 ID)

**lid (Merge Field Name Language ID)**

=== "中文"

=== "英文"

## 17.14.18 linkToQuery (查询包含外部查询文件的链接)

**linkToQuery (Query Contains Link to External Query File)**

=== "中文"

=== "英文"

## 17.14.19 mailAsAttachment (合并文档至电子邮件附件)

**mailAsAttachment (Merged Document To E-Mail Attachment)**

=== "中文"

=== "英文"

## 17.14.20 mailMerge (邮件合并设置)

**mailMerge (Mail Merge Settings)**

=== "中文"

=== "英文"

## 17.14.21 mailSubject (合并电子邮件或传真主题行)

**mailSubject (Merged E-mail or Fax Subject Line)**

=== "中文"

=== "英文"

## 17.14.22 mainDocumentType (源文档类型)

**mainDocumentType (Source Document Type)**

=== "中文"

=== "英文"

## 17.14.23 mappedName (预定义合并字段名称)

**mappedName (Predefined Merge Field Name)**

=== "中文"

=== "英文"

## 17.14.24 name (列的数据源名称)

**name (Data Source Name for Column)**

=== "中文"

=== "英文"

## 17.14.25 odso (Office 数据源对象设置)

**odso (Office Data Source Object Settings)**

=== "中文"

=== "英文"

## 17.14.26 query (查询要合并的数据源记录)

**query (Query For Data Source Records To Merge)**

=== "中文"

=== "英文"

## 17.14.27 recipientData (关于单个数据源记录的数据)

**recipientData (Data About Single Data Source Record)**

=== "中文"

=== "英文"

## 17.14.28 recipientData (参考数据源的包含/排除数据)

**recipientData (Reference to Inclusion/Exclusion Data for Data Source)**

=== "中文"

=== "英文"

## 17.14.29 recipients (数据源的包含/排除数据)

**recipients (Inclusion/Exclusion Data for Data Source)**

=== "中文"

=== "英文"

## 17.14.30 src (ODSO 数据源文件路径)

**src (ODSO Data Source File Path)**

=== "中文"

=== "英文"

## 17.14.31 table (数据源表名称)

**table (Data Source Table Name)**

=== "中文"

=== "英文"

## 17.14.32 type (ODSO 数据源类型)

**type (ODSO Data Source Type)**

=== "中文"

=== "英文"

## 17.14.33 type (合并字段映射)

**type (Merge Field Mapping)**

=== "中文"

=== "英文"

## 17.14.34 udl (UDL 连接字符串)

**udl (UDL Connection String)**

=== "中文"

=== "英文"

## 17.14.35 uniqueTag (记录的唯一值)

**uniqueTag (Unique Value for Record)**

=== "中文"

=== "英文"

## 17.14.36 viewMergedData (查看文档中的合并数据)

**viewMergedData (View Merged Data Within Document)**

=== "中文"

=== "英文"
