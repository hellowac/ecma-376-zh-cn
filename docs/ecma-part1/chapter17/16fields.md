# 17.16 字段和超链接

**Fields and Hyperlinks**

=== "中文"

    在文字处理文档中，大部分文本是静态的；即除非直接通过编辑更改，其内容会保持不变，无论文档的其余部分如何变化。然而，某些有用的信息在文档生命周期内可能会改变。例如页码引用：“有关更多信息，请参见第 56 页。”显然，将页码硬编码为 56 意味着在文档大小或布局发生变化时需要手动更换该数字。即使是对页边距、行距或字体大小的简单更改也会使此类引用失效。

    字段提供了一种占位符机制，如页码引用，可以添加到文档中，使这些占位符在文档显示或打印时由相应的值替换。字段的其他应用包括但不限于表格和图形的自动编号、文档创建日期和当前日期时间、文档作者信息以及表格列的总计计算。
    
    字段是一组代码，指示 WordprocessingML 消费者自动将文本、图形、页码等内容插入文档。[示例：DATE 字段会插入当前日期。结束示例] 当消费者执行字段代码时插入到文档中的文本或图形称为该字段的字段结果（或字段值）。字段结果的默认值是空字符串。执行字段代码的行为称为字段更新。字段更新应当进行，以使字段结果中的内容正确反映字段代码的预期语义（如 [§17.16.5] 的子条款中所定义）。对于通过 fldSimple 元素定义的简单字段（[§17.16.19]），这意味着将其子元素替换为适当的 WordprocessingML 内容；对于通过正确匹配的 fldChar 元素表示的复杂字段（[§17.16.18]），这意味着替换 fldChar 元素之间的任何内容，该 fldChar 元素具有 fldCharType 属性值 separate 和 fldCharType 属性值 end。至于何时更新字段，不在 ECMA-376 的范围之内。

=== "英文"
    
    Most text in a word processing document is static; that is, unless it is directly changed as the result of editing, its contents remain the same, no matter how the rest of the document might change. However, certain useful pieces of information can change value over the life of a document. Consider the case of a reference to a page number, as in "For more information on this topic, see page 56." Clearly, hard coding the page number as 56 means that that number needs to be manually replaced as the document's size or layout is changed. Even a simple change to any margin, line spacing, or font size can invalidate such references.
    
    Fields provide a mechanism for placeholders, such as page reference numbers, that can be added to a document such that those placeholders are replaced by their corresponding values when the document is rendered for display or print. Other applications for fields include, but are not limited to, automatic numbering of tables and figures, document creation and current date and time, document author information, and the computation of totals for a table column.
    
    A field is a set of codes that instructs a WordprocessingML consumer to insert text, graphics, page numbers, and other material into a document automatically. [Example: The DATE field causes the current date to be inserted. end example] The text or graphics inserted into a document when a consumer carries out a field's codes is referred to as the field result (or field value) for that field. The default value for a field result is an empty string. The act of carrying out a field's codes is referred to as a field update. A field update shall be carried out such that the content contained within the field result correctly reflects the intended semantics of the field codes (as defined in the subclauses of [§17.16.5]). For a simple field defined via the fldSimple element ([§17.16.19]), this means replacing its child elements with the appropriate WordprocessingML content; for a complex field represented by use of properly matched fldChar elements ([§17.16.18]), this means replacing any content between the fldChar element with an fldCharType attribute value of separate and an fldCharType attribute value of end. As to when any field is updated is outside the scope of ECMA-376.

## 17.16.1 语法

**Syntax**

=== "中文"
    
    在本小节中，语法规则遵循 ISO/IEC 14977 中所示的系统：文本文字用双引号（或撇号）括起来；左方括号和右方括号表示选项的开始和结束；左大括号和右大括号表示一个或多个项目的序列的开始和结束；竖线表示替代项；每个规则以分号结束。每当连字符用作异常符号时（按照 ISO/IEC 14977 的规定），它都被空格括起来，并且通过注释进一步进行澄清。
    
    下面的语法规则源自于在详细定义中显示的字段特定规则，即 §17.16.5.\* 中的规则。
    【注意：为了生成自动验证器，还必须考虑 17.16.5.\* 小节中的字段特定规则。结束注意】
    
    在叙述中使用时，产生名以斜体样式呈现，如 *comparison*、*field-argument* 和 *switches*。
    
    字段的语法如下：
    
    ```text
    field=
        field-type, [switches] ;
    field-type=
        date-and-time |
        document-automation |
        document-information |
        document-property |
        equations-and-formulas |
        index-and-tables |
        links-and-references |
        mail-merge |
        numbering |
        user-information |
        form-field |    user-defined-field;
    user-defined-field=
        letter, {letter} ;
    date-and-time=
        "CREATEDATE" | "DATE" | "EDITTIME" | "PRINTDATE" |
        "SAVEDATE" | "TIME" ;
    document-automation=
        "COMPARE", comparison |
        "DOCVARIABLE", field-argument |
        "GOTOBUTTON", 2 * field-argument |
        "IF", comparison, 2 * field-argument |
        "MACROBUTTON", 2 * field-argument |
        "PRINT", field-argument |
        "PRIVATE" ;
    document-information=
        "FILENAME" | "FILESIZE" | "LASTSAVEDBY" | "NUMCHARS"
        "NUMPAGES" | "NUMWORDS" | "TEMPLATE" ;
    document-property=
        "AUTHOR", [field-argument] |
        "COMMENTS", [field-argument] |
        "DOCPROPERTY", docprop-category |
        "KEYWORDS", [field-argument] |
        "SUBJECT", [field-argument] |
        "TITLE", [field-argument] ;
    equations-and-formulas=
        "=", expression |
        "ADVANCE" |
        "SYMBOL", field-argument ;
    index-and-tables=
        "INDEX" |
        "RD", field-argument |
        "TA" |
        "TC", field-argument |
        "TOA" |
        "TOC" |
        "XE", field-argument ;
    links-and-references=
        "AUTOTEXT", field-argument |
        "AUTOTEXTLIST", field-argument |
        "BIBLIOGRAPHY" |
        "CITATION", field-argument |
        "HYPERLINK", field-argument |
        "INCLUDEPICTURE", field-argument |
        "INCLUDETEXT", field-argument, [field-argument] |
        "LINK", 2 * field-argument, [field-argument] |
        "NOTEREF", field-argument |
        "PAGEREF", field-argument |
        "QUOTE", field-argument |
        ["REF"], field-argument | (* see [§17.16.5.51] *)
        "STYLEREF", field-argument ;
    mail-merge=
        "ADDRESSBLOCK" |
        "ASK", 2 * field-argument |
        "DATABASE" |
        "FILLIN", [field-argument] |
        "GREETINGLINE" |
        "MERGEFIELD", field-argument |
        "MERGEREC" |
        "MERGESEQ" |
        "NEXT" |
        "NEXTIF", comparison |
        "SET", 2 * field-argument |
        "SKIPIF", comparison ;
    numbering=
        "LISTNUM", [field-argument] |
        "PAGE" |
        "REVNUM" |
        "SECTION" |
        "SECTIONPAGES" |
        "SEQ", identifier, [field-argument] ;
    user-information=
        "USERADDRESS", [field-argument] |
        "USERINITIALS", [field-argument] |
        "USERNAME", [field-argument] ;
    form-field=
        "FORMCHECKBOX" | "FORMDROPDOWN" | "FORMTEXT" ;
    bookmark-name=
        identifier ;
    cell-name=
        column-name, row-name ;
    cell-range=
        cell-name, colon, cell-name |
        row-name, colon, row-name |
        column-name, colon, column-name ;
    cell-reference=
        cell-name |
        cell-name, { comma, cell-name } |
        cell-range ;
    character=
        as defined by the production Char in the XML 1.0 specification, §2.2.
    colon=
        ":" ;
    column-name=
        letter + [{letter}] ;
    (* allowing for A, … Z, AA, …., ZZ, AAA, … column naming *)
    comma=
        ","    ;
    comparison=
        expression, comparison-operator, expression ;
    comparison-operator=
        "=" | "<>" | "<" | "<=" | ">" | ">=" ;
    constant=
        number ;
    date-and-time-formatting-switch=
        "\@", switch-argument (* as defined in [§17.16.4.1] *) ;
    docprop-category=
        "AUTHOR" | "BYTES" | "CATEGORY" | "CHARACTERS" |
        "CHARACTERSWITHSPACES" | "COMMENTS" |
        "COMPANY | CREATETIME" | "HYPERLINKBASE" |
        "KEYWORDS" | "LASTPRINTED" | "LASTSAVEDBY" |
        "LASTSAVEDTIME" | "LINES" | "MANAGER" |
        "NAMEOFAPPLICATION" | "ODMADOCID" | "PAGES" |
        "PARAGRAPHS" | "REVISIONNUMBER"| "SECURITY" |
        "SUBJECT" | "TEMPLATE" | "TITLE" |
        "TOTALEDITINGTIME" | "WORDS" ;
    double-quote=
        '"'    ; (* one double-quote character *)
    expression=
        "(", expression, ")" |
        comparison |
        constant |
        prefix-operator, expression |
        expression, infix-operator, expression |
        field |
        bookmark-name, [cell-reference] |
        function |
        cell-reference |
        text |
        double-quote, text, double-quote ;
    field-argument=
        text |
        double-quote, text, double-quote ;
    field-specific-switch=
        "\", character, [character], [field-argument] ;
            (* no whitespace is permitted after the backslash,
            also see definition of each field in [§17.16.5] *)
    formatting-switch=
        date-and-time-formatting-switch |
        numeric-formatting-switch |
        general-formatting-switch ;
    fractional-part=
        decimal-digit {decimal-digit} ;
    full-stop=
        "."    ; (* also known as “period” *)
    function=
        "ABS(", expression, ")" |
        "AND(", expression, "," expression, ")" |
        "AVERAGE(", list, ")" |
        "COUNT(", list, ")" |
        "DEFINED(", expression, ")" |
        "FALSE" |
        "INT(", expression, ")" |
        "MAX(", list, ")" |
        "MIN(", list, ")" |
        "MOD(", expression, ",", expression, ")" |
        "NOT(", expression, ")" |
        "OR(", expression, ",", expression, ")" |
        "PRODUCT(", list, ")" |
        "ROUND(", expression, ",", expression, ")" |
        "SIGN(", expression, ")" |
        "SUM(", list, ")" |
        "TRUE" ;
    general-formatting-switch=
        "\*", switch-argument ; (* as defined in [§17.16.4.3] *)
    identifier=
        character + [{character}] ;
    infix-operator=
        "-" | "^" | "*" | "/" | "%" | "+" | "-" | "=" |
        "<>" | "<" | "<=" | ">" | ">=" ; (* see [§17.16.3.3] *)
    letter=
        "a"|"b"|"c"|"d"|"e"|"f"|"g"|"h"|"i"|"j"|"k"|"l"|"m"|
        "n"|"o"|"p"|"q"|"r"|"s"|"t"|"u"|"v"|"w"|"x"|"y"|"z"|
        "A"|"B"|"C"|"D"|"E"|"F"|"G"|"H"|"I"|"J"|"K"|"L"|"M"|
        "N"|"O"|"P"|"Q"|"R"|"S"|"T"|"U"|"V"|"W"|"X"|"Y"|"Z" ;
    list=
        expression, {list-separator, expression} ;
    list-separator=
        comma | semicolon ;
            (* depending on the document’s listSeparator, [§17.15.1.56]*)
    number=
        whole-number-part, [full-stop] |
        full-stop, fractional-part |
        whole-number-part, full-stop, fractional-part ;
    numeric-formatting-switch=
        "\#", switch-argument ;    (* as defined in [§17.16.4.2] *)
    prefix-operator=
        "-" ;
    row-name=
        whole-number-part ;
    semicolon=
        ";"    ;
    switch-argument=
        text |
        double-quote, text, double-quote ;
    switches=
        {field-specific-switch}, [formatting-switch]
    text=
        character, {character} ;
    whole-number-part=
        decimal-digit, {decimal-digit} ;
    ```
    
    公式（也称为表达式）在[§17.16.3]中进行了讨论，常量在[§17.16.3.1]中进行了讨论，书签在[§17.16.3.2]中进行了讨论，运算符在[§17.16.3.3]中进行了讨论，函数在[§17.16.3.4]中进行了讨论，表格单元引用在[§17.16.3.5]中进行了讨论，格式开关在[§17.16.4]中进行了讨论。
    
    具有*用户定义字段类型*的字段的语义未指定。
    
    如果*字段参数*或*开关参数*中的*文本*包含空格，则分隔双引号字符必须存在；否则，它们是可选的。要在*文本*中包含双引号字符，必须在其前面加上反斜杠（\\）。【示例：字段参数 "\"name\"" 的结果是实际参数为 "name"。结束示例】要在文本中包含反斜杠字符，必须在其前面加上另一个反斜杠（\\）。【示例：某些系统上的文件系统路径名使用反斜杠作为目录分隔符，如在字段
    
    ```text
    INCLUDETEXT "E:\\ReadMe.txt"
    ```
    
    中，每个这样的分隔符都需要在前面加上一个反斜杠，如上所示。结束示例】
    
    在第一个标记之前、最后一个标记之后以及连续标记之间，包括没有任何空白字符在内，都可以出现任意数量的空白字符，但在*字段特定开关*中，不允许在初始“\”标记和后面的*字符*之间有任何空白字符。
    
    【示例：以下是一些字段的示例：
    
    ```xml
    DATE
    DATE \@ "dddd, MMMM dd, yyyy"
    DATE \@ "dddd, MMMM dd, yyyy" \h
    ```
    
    所有三个的字段结果都是今天的日期：第一个字段使用了一些实现定义的格式和公历；第二个字段使用了指定的格式和公历；第三个字段使用了指定的格式和伊斯兰教历。在2005年12月31日的美国英语环境中呈现时，这些字段的结果如下：
    
    ```text
    12/31/2005
    Saturday, December 31, 2005
    AsSabt, Thoul Ki'dah 30, 1426
    ```
    
    结束示例】
    
    字段的名称是字母令牌【示例：一些字段类型名称是 ASK、COMMENTS、NEXT 和 SET。结束示例】。这些标记称为字段类型名称。字段类型名称是大小写不敏感的【示例：字段类型名称 DATE、Date、dAtE 和 date 是等效的。结束示例】
    
    在*字段特定开关*中，“\”后面紧跟的*字符*是不区分大小写的【示例：`\b` 和 `\B` 是等效的。结束示例】
    
    开关中的*字段特定开关*条目没有顺序。

=== "英文"
    
    The syntax rules in this subclause follow the system shown in ISO/IEC 14977: literal text is surrounded by
    double-quotes (or by apostrophes); the left-square-bracket and right-square-bracket designate the start and end
    of an option; the left-curly-bracket and right-curly-bracket designate the start and end of a sequence of one-or-
    more items; the vertical-line indicates an alternative; and each rule ends with a semicolon. Whenever hyphen is
    used as the exception-symbol (as per ISO/IEC 14977), it is surrounded by white space, and further clarified by a
    comment.
    
    The syntax rules below were derived from the field-specific rules in the detailed definitions shown in §17.16.5.\*.
    [Note: In order to produce an automated verifier, field-specific rules in subclauses 17.16.5.\* must also be
    considered. end note]
    
    When used in narrative, production names are set in an italic style, as in *comparison*, *field-argument*, and
    *switches*.
    
    The syntax of a field is as follows:
    
    ```text
    field=
        field-type, [switches] ;
    field-type=
        date-and-time |
        document-automation |
        document-information |
        document-property |
        equations-and-formulas |
        index-and-tables |
        links-and-references |
        mail-merge |
        numbering |
        user-information |
        form-field |    user-defined-field;
    user-defined-field=
        letter, {letter} ;
    date-and-time=
        "CREATEDATE" | "DATE" | "EDITTIME" | "PRINTDATE" |
        "SAVEDATE" | "TIME" ;
    document-automation=
        "COMPARE", comparison |
        "DOCVARIABLE", field-argument |
        "GOTOBUTTON", 2 * field-argument |
        "IF", comparison, 2 * field-argument |
        "MACROBUTTON", 2 * field-argument |
        "PRINT", field-argument |
        "PRIVATE" ;
    document-information=
        "FILENAME" | "FILESIZE" | "LASTSAVEDBY" | "NUMCHARS"
        "NUMPAGES" | "NUMWORDS" | "TEMPLATE" ;
    document-property=
        "AUTHOR", [field-argument] |
        "COMMENTS", [field-argument] |
        "DOCPROPERTY", docprop-category |
        "KEYWORDS", [field-argument] |
        "SUBJECT", [field-argument] |
        "TITLE", [field-argument] ;
    equations-and-formulas=
        "=", expression |
        "ADVANCE" |
        "SYMBOL", field-argument ;
    index-and-tables=
        "INDEX" |
        "RD", field-argument |
        "TA" |
        "TC", field-argument |
        "TOA" |
        "TOC" |
        "XE", field-argument ;
    links-and-references=
        "AUTOTEXT", field-argument |
        "AUTOTEXTLIST", field-argument |
        "BIBLIOGRAPHY" |
        "CITATION", field-argument |
        "HYPERLINK", field-argument |
        "INCLUDEPICTURE", field-argument |
        "INCLUDETEXT", field-argument, [field-argument] |
        "LINK", 2 * field-argument, [field-argument] |
        "NOTEREF", field-argument |
        "PAGEREF", field-argument |
        "QUOTE", field-argument |
        ["REF"], field-argument | (* see [§17.16.5.51] *)
        "STYLEREF", field-argument ;
    mail-merge=
        "ADDRESSBLOCK" |
        "ASK", 2 * field-argument |
        "DATABASE" |
        "FILLIN", [field-argument] |
        "GREETINGLINE" |
        "MERGEFIELD", field-argument |
        "MERGEREC" |
        "MERGESEQ" |
        "NEXT" |
        "NEXTIF", comparison |
        "SET", 2 * field-argument |
        "SKIPIF", comparison ;
    numbering=
        "LISTNUM", [field-argument] |
        "PAGE" |
        "REVNUM" |
        "SECTION" |
        "SECTIONPAGES" |
        "SEQ", identifier, [field-argument] ;
    user-information=
        "USERADDRESS", [field-argument] |
        "USERINITIALS", [field-argument] |
        "USERNAME", [field-argument] ;
    form-field=
        "FORMCHECKBOX" | "FORMDROPDOWN" | "FORMTEXT" ;
    bookmark-name=
        identifier ;
    cell-name=
        column-name, row-name ;
    cell-range=
        cell-name, colon, cell-name |
        row-name, colon, row-name |
        column-name, colon, column-name ;
    cell-reference=
        cell-name |
        cell-name, { comma, cell-name } |
        cell-range ;
    character=
        as defined by the production Char in the XML 1.0 specification, §2.2.
    colon=
        ":" ;
    column-name=
        letter + [{letter}] ;
    (* allowing for A, … Z, AA, …., ZZ, AAA, … column naming *)
    comma=
        ","    ;
    comparison=
        expression, comparison-operator, expression ;
    comparison-operator=
        "=" | "<>" | "<" | "<=" | ">" | ">=" ;
    constant=
        number ;
    date-and-time-formatting-switch=
        "\@", switch-argument (* as defined in [§17.16.4.1] *) ;
    docprop-category=
        "AUTHOR" | "BYTES" | "CATEGORY" | "CHARACTERS" |
        "CHARACTERSWITHSPACES" | "COMMENTS" |
        "COMPANY | CREATETIME" | "HYPERLINKBASE" |
        "KEYWORDS" | "LASTPRINTED" | "LASTSAVEDBY" |
        "LASTSAVEDTIME" | "LINES" | "MANAGER" |
        "NAMEOFAPPLICATION" | "ODMADOCID" | "PAGES" |
        "PARAGRAPHS" | "REVISIONNUMBER"| "SECURITY" |
        "SUBJECT" | "TEMPLATE" | "TITLE" |
        "TOTALEDITINGTIME" | "WORDS" ;
    double-quote=
        '"'    ; (* one double-quote character *)
    expression=
        "(", expression, ")" |
        comparison |
        constant |
        prefix-operator, expression |
        expression, infix-operator, expression |
        field |
        bookmark-name, [cell-reference] |
        function |
        cell-reference |
        text |
        double-quote, text, double-quote ;
    field-argument=
        text |
        double-quote, text, double-quote ;
    field-specific-switch=
        "\", character, [character], [field-argument] ;
            (* no whitespace is permitted after the backslash,
            also see definition of each field in [§17.16.5] *)
    formatting-switch=
        date-and-time-formatting-switch |
        numeric-formatting-switch |
        general-formatting-switch ;
    fractional-part=
        decimal-digit {decimal-digit} ;
    full-stop=
        "."    ; (* also known as “period” *)
    function=
        "ABS(", expression, ")" |
        "AND(", expression, "," expression, ")" |
        "AVERAGE(", list, ")" |
        "COUNT(", list, ")" |
        "DEFINED(", expression, ")" |
        "FALSE" |
        "INT(", expression, ")" |
        "MAX(", list, ")" |
        "MIN(", list, ")" |
        "MOD(", expression, ",", expression, ")" |
        "NOT(", expression, ")" |
        "OR(", expression, ",", expression, ")" |
        "PRODUCT(", list, ")" |
        "ROUND(", expression, ",", expression, ")" |
        "SIGN(", expression, ")" |
        "SUM(", list, ")" |
        "TRUE" ;
    general-formatting-switch=
        "\*", switch-argument ; (* as defined in [§17.16.4.3] *)
    identifier=
        character + [{character}] ;
    infix-operator=
        "-" | "^" | "*" | "/" | "%" | "+" | "-" | "=" |
        "<>" | "<" | "<=" | ">" | ">=" ; (* see [§17.16.3.3] *)
    letter=
        "a"|"b"|"c"|"d"|"e"|"f"|"g"|"h"|"i"|"j"|"k"|"l"|"m"|
        "n"|"o"|"p"|"q"|"r"|"s"|"t"|"u"|"v"|"w"|"x"|"y"|"z"|
        "A"|"B"|"C"|"D"|"E"|"F"|"G"|"H"|"I"|"J"|"K"|"L"|"M"|
        "N"|"O"|"P"|"Q"|"R"|"S"|"T"|"U"|"V"|"W"|"X"|"Y"|"Z" ;
    list=
        expression, {list-separator, expression} ;
    list-separator=
        comma | semicolon ;
            (* depending on the document’s listSeparator, [§17.15.1.56]*)
    number=
        whole-number-part, [full-stop] |
        full-stop, fractional-part |
        whole-number-part, full-stop, fractional-part ;
    numeric-formatting-switch=
        "\#", switch-argument ;    (* as defined in [§17.16.4.2] *)
    prefix-operator=
        "-" ;
    row-name=
        whole-number-part ;
    semicolon=
        ";"    ;
    switch-argument=
        text |
        double-quote, text, double-quote ;
    switches=
        {field-specific-switch}, [formatting-switch]
    text=
        character, {character} ;
    whole-number-part=
        decimal-digit, {decimal-digit} ;
    ```
    
    Formulas (also called expressions) are discussed in [§17.16.3], constants are discussed in [§17.16.3.1], bookmarks are discussed in [§17.16.3.2], operators are discussed in [§17.16.3.3], functions are discussed in [§17.16.3.4], table cell references are discussed in [§17.16.3.5], and formatting switches are discussed in [§17.16.4].
    
    The semantics of a field having a *user-defined-field type* are unspecified.
    
    If the *text* in a *field-argument* or *switch-argument* contains white space, the delimiting double-quote characters shall be present; otherwise, they are optional. To include a double-quote character in *text*, it shall be preceded with a backslash (\\). [Example: The field argument "\"name\"" results in the argument's actually being "name". end example] To include a backslash character in text, it shall be preceded with another backslash (\\). [Example: File system pathnames on some systems use a backslash as a directory separator, as in the field 
    ```text
    INCLUDETEXT "E:\\ReadMe.txt"
    ```
    
    in which case, each such separator needs to be preceded with a backslash, as shown above. end example]
    
    Arbitrary amount of white space can occur before the first token, after the last token, and between successive tokens, including no white space at all, except that in a *field-specific-switch*, no white space is permitted between the initial “\” token and the *character* that follows it.
    
    [Example: Here are examples of some fields:
    
    ```xml
    DATE
    DATE \@ "dddd, MMMM dd, yyyy"
    DATE \@ "dddd, MMMM dd, yyyy" \h
    ```
    
    The field result of all three is today's date: The first field uses some implementation-defined format and the Gregorian calendar; the second field uses the specified format and the Gregorian calendar; and the third field uses the specified format and the Hijri lunar calendar. When rendered in a US-English context on December 31, 2005, the results of these fields were as follows:
    
    ```text
    12/31/2005
    Saturday, December 31, 2005
    AsSabt, Thoul Ki'dah 30, 1426
    ```
    
    end example]
    
    The names of fields are alphabetic tokens [Example: Some field-type names are ASK, COMMENTS, NEXT, and SET. end example]. These tokens are called field-type names. Field-type names are case-insensitive. [Example: The field-type names DATE, Date, dAtE, and date are equivalent. end example]
    
    The *characters* immediately following the “\” in *field-specific-switchare* case-insensitive. [Example: `\b` and `\B`
    are equivalent. end example]
    
    There is no ordering of *field-specific-switch* entries in switches.

## 17.16.2 XML表示

**XML representation**

=== "中文"
    
    字段应该通过以下两种方法之一在XML中实现：
    
    - 作为简单字段实现，使用fldSimple元素，或者
    - 作为复杂字段实现，使用一组包含fldChar和instrText元素的运行。
    
    对于简单字段实现，只能使用一个元素，即fldSimple，其中，它的instr属性应包含一个字段，并且该元素的主体应包含最近更新的字段结果。【示例：以下是DATE的简单字段实现的相应XML：
    
    ```xml
    <w:fldSimple w:instr="DATE">
        <w:r>
            <w:t>12/31/2005</w:t>
        </w:r>
    </w:fldSimple>
    ```
    
    结束示例】
    
    对于复杂字段实现，应使用一组运行，每个运行依次包含以下元素：
    
    - 带有属性fldCharType值为begin的fldChar，
    - 一个或多个instrText元素，这些元素集体包含完整的字段，
    - 可选地，
        - 带有属性fldCharType值为separate的fldChar，将字段与其字段结果分隔开，
        - 包含最近更新的字段结果的任意数量的运行和段落，
    - 带有属性fldCharType值为end的fldChar。
    
    【注意：仅用于显示目的的字段不需要且不会存储字段结果。结束注意】【示例：以下是DATE的复杂字段实现的相应XML：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> DATE </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>12/31/2005</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    结束示例】
    
    【注意：对于给定字段的每个简单字段实现都有一个相应的复杂字段实现。但是，并非每个复杂字段实现都有相应的简单字段实现。如果字段中的一些字符具有不同于其他字符的运行属性，则必须使用多个运行来实现该字段，并且需要使用复杂字段实现。例如，请参阅[§17.16.4.3]，其中DATE字段的第一个字母被设置为粗体、下划线和红色，而其他字母则没有这些属性。结束注意】
    
    如[§17.16.1]所示，一个字段的*指令(instruction)*可以是另一个*字段(field)*，从而允许字段嵌套。在这种情况下，内部字段的XML运行序列在该内部字段的引用点内部定义，在外部字段的XML运行序列内部。【示例：考虑以下句子：
    
    ```text
    It's IF DATE \@ "M-d"<>"1-1" "not " new year's day.
    ```
    
    IF字段包含嵌套的DATE \@ "M-d" 字段。在更新时，在任何一年的1月1日，结果句子是 "It's new year's day." 在一年的其他日期，结果句子是"It's not new year's day." 
    
    以下是编写相应XML的一种方式：
    
    ```xml
    <w:r>
        <w:t xml:space="preserve">It’s </w:t>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">IF </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> DATE \@ "M-d" </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:instrText>1-4</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    <w:r>
        <w:instrText>&lt;&gt;"1-1" "not "</w:instrText>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t xml:space="preserve">not </w:t>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    <w:r>
        <w:t>new year’s day!</w:t>
    </w:r>
    ```
    
    end example】

=== "英文"
    
    Fields shall be implemented in XML using either of two approaches:
    
    - As a simple field implementation, using the fldSimple element, or
    - As a complex field implementation, using a set of runs involving the fldChar and instrText elements.
    
    For a simple field implementation, only one element, fldSimple, shall be used, in which case, its instr attribute shall contain a field, and the body of the element shall contain the most recently updated field result. [Example: Here is the corresponding XML for a simple field implementation of DATE:
    
    ```xml
    <w:fldSimple w:instr="DATE">
    <w:r>
    <w:t>12/31/2005</w:t>
    </w:r>
    </w:fldSimple>
    ```
    
    end example]
    
    For a complex field implementation, a set of runs shall be used with each run containing, in sequence, the following elements:
    
    
    - fldChar with attribute fldCharType value begin,
    - One or more instrText elements, which, collectively, contain a complete field,
    - Optionally,
        - fldChar with attribute fldCharType value separate, which separates the field from its field result,
        - Any number of runs and paragraphs that contains the most recently updated field result, and
    - fldChar with attribute fldCharType value end.
    
    [Note: Fields that are for display purposes only have no need to, and do not, store a field result. end note][Example: Here is the corresponding XML for a complex field implementation of DATE:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> DATE </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>12/31/2005</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    end example]
    
    [Note: Every simple field implementation for a given field has a corresponding complex field implementation. However, not every complex field implementation has a corresponding simple field implementation. If some characters in a field have different run properties than others, that field must be implemented using multiple runs, and that requires that complex field implementation be used. For an example, see [§17.16.4.3], where the first letter of a DATE field is made bold, underlined, and red, while the other letters have none of these properties. end note]
    
    As shown in [§17.16.1], the *instruction* of one *field* can be another *field*, allowing fields to nest. In such cases, the XML run sequence for the inner field is defined at the point of reference for that inner field, inside the outer field's XML run sequence. [Example: Consider the following sentence:
    
    ```text
    It's IF DATE \@ "M-d"<>"1-1" "not " new year's day.
    ```
    
    The IF field contains the nested field DATE \@ "M-d". When updated, on January 1 of any year, the result sentence is "It's new year's day." On all other days of the year, the resulting sentence is "It's not new year's day." 
    
    Here is one way of writing the corresponding XML:
    
    ```xml
    <w:r>
        <w:t xml:space="preserve">It’s </w:t>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">IF </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> DATE \@ "M-d" </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:instrText>1-4</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    <w:r>
        <w:instrText>&lt;&gt;"1-1" "not "</w:instrText>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t xml:space="preserve">not </w:t>
    </w:r>
    <w:r …>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    <w:r>
        <w:t>new year’s day!</w:t>
    </w:r>
    ```
    
    end example]

## 17.16.3 公式和表达式

**Formulas and expressions**

=== "中文"
    
    字段指令可以通过公式进行计算，公式简单地说是一个任意复杂的算术表达式，涉及常数([§17.16.3.1])、引用表达式的书签([§17.16.3.2])、算术和逻辑运算符([§17.16.3.3])、函数([§17.16.3.4])、表格中单元格的值([§17.16.3.5])以及产生单个值的字段。表达式可以包含分组括号，以记录默认优先级或覆盖它。
    
    表达式中的所有算术项都是实数。不支持无穷大和NaN（非数值）。【示例：在表达式1/3中，尽管操作数看起来是整数，但实际上它们是实数，结果是0.33。】

=== "英文"
    
    A field instruction can involve a calculation via a formula, which is simply an expression that is an arbitrary complex arithmetic expression involving constants ([§17.16.3.1]), bookmarks that refer to expressions ([§17.16.3.2]), arithmetic and logical operators ([§17.16.3.3]), functions ([§17.16.3.4]), values of cells in a table ([§17.16.3.5]), and fields that result in a single value. expression can contain grouping parentheses to document the default precedence or to override it.
    
    All arithmetic terms in an expression are real numbers. Infinities and NaN (Not-a-Number) are not supported. [Example: In the expression 1/3, although the operands appear to be integers, they are, in fact real numbers, and the result is 0.33. end example]

### 17.16.3.1 常量

**Constants**

=== "中文"

    常数(常量)是一个数字。不支持指数。
    
    【示例：以下是一些常数：1234、1234.560、1234.、和.1234。】

=== "英文"

    A constant is a number. Exponents are not supported.
        
    [Example: Here are some constants: 1234, 1234.560, 1234., and .1234. end example]

### 17.16.3.2 书签

**Bookmarks**

=== "中文"

    WordprocessingML 文档中的任意文本和/或图形都可以被分配一个名称，称为书签(bookmark)。如果一个书签引用代表表达式的文本，那么该书签的名称可以作为另一个表达式的操作数。如果一个整个字段被标记为书签，那么它的书签名称也可以作为表达式中的操作数。【示例：假设 X 是文本 4 的书签，Y 是文本 2 的书签，Result 是以下字段的书签：
    
    ```text
    =X + Y
    ```
    
    那么字段
    
    ```text
    =Result * 10
    ```
    
    的结果是 60。】

=== "英文"

    Any arbitrary piece of text and/or graphics in a WordprocessingML document can be assigned a name, called a bookmark. If a bookmark references text that represents an expression, that bookmark's name can be used as an operand in another expression. If a whole field is bookmarked, its bookmark name can also be used as an operand in an expression. [Example: Given that X is a bookmark for the text 4, Y is a bookmark for the text 2, and Result is a bookmark for the following field:
    
    ```text
    =X + Y
    ```
    
    the field
    
    ```text
    =Result * 10
    ```
    
    has the result 60. end example]

### 17.16.3.3 运算

**Operators**

=== "中文"
    
    在*表达式*中允许的*运算符*如下：
    
    | **运算符** | **描述** | **优先级** |
    | ---------- | -------- | ---------- |
    | -          | 一元     | 最高       |
    | ^          | 幂和根   |            |
    | *          | 乘法     |            |
    | /          | 除法     |            |
    | %          | 百分比   |            |
    | +          | 加法     |            |
    | -          | 减法     |            |
    | =          | 等于     |            |
    | <>         | 不等于   |            |
    | <          | 小于     | 最低       |
    | <=         | 小于等于 |            |
    | >          | 大于     |            |
    | >=         | 大于等于 |            |
    
    *表达式*中具有相同优先级的运算符从左到右进行关联。
    
    【示例：假设X是文本4的书签，Y是文本2的书签，则以下字段
    
    ```text
    =((-1 + X^2) * 3 - Y)/2
    ```
    
    产生结果21.5。】 
    
    相等、不等和关系运算符为真时返回1，为假时返回0。值为0的表达式在逻辑上测试为假，而任何非零值的表达式在逻辑上测试为真。

=== "英文"
    
    The *operators* permitted in *expression* are:
    
    <table border="1">
        <tr>
            <td colspan="3">Operators</td>
        </tr>
        <tr>
            <td>Operator</td>
            <td>Description</td>
            <td>Precedence</td>
        </tr>
        <tr>
            <td>-</td>
            <td>Unary</td>
            <td>minushighest</td>
        </tr>
        <tr>
            <td>^</td>
            <td>Powers and roots</td>
            <td></td>
        </tr>
        <tr>
            <td>*</td>
            <td>Multiplication</td>
            <td></td>
        </tr>
        <tr>
            <td>/</td>
            <td>Division</td>
            <td></td>
        </tr>
        <tr>
            <td>%</td>
            <td>Percentage </td>
            <td></td>
        </tr>
        <tr>
            <td>+</td>
            <td>Addition </td>
            <td></td>
        </tr>
        <tr>
            <td>-</td>
            <td>Subtraction </td>
            <td></td>
        </tr>
        <tr>
            <td>=</td> 
            <td>Equal to</td> 
            <td></td>
        </tr>
        <tr>
            <td>&lt;&gt;</td> 
            <td>Not  equal to</td> 
            <td></td>
        </tr>
        <tr>
            <td>&lt;</td>
            <td>Less than</td>   
            <td>lowest</td>
        </tr>
        <tr>
            <td>&lt;=</td>
            <td>Less than or equal to</td> 
            <td></td>
        </tr>
        <tr>
            <td>&gt;</td>
            <td>Greater than</td> 
            <td></td>
        </tr>
        <tr>
            <td>&gt;=</td>
            <td>Greater than or equal to</td> 
            <td></td>
        </tr>
    </table>
    
    Operators in *expression* having the same precedence associate left-to-right.
    
    [Example: Given that X is a bookmark for the text 4, and Y is a bookmark for the text 2, the field
    
    ```text
    =((-1 + X^2) * 3 - Y)/2
    ```
    
    produces the result 21.5. end example]
    
    The equality, inequality, and relational operators yield 1 for true and 0 for false. An expression with value 0 tests logically false while one with any non-zero value tests true.

### 17.16.3.4 函数

**Functions**

=== "中文"
    
    函数是预定义的过程，用于计算并返回结果。下面定义的函数，具有参数列表的列表，接受两个或更多参数，参数之间用逗号(,)或分号(;)分隔。允许使用哪种分隔符由文档的listSeparator（[§17.15.1.56]）元素定义。函数的参数可以是常量、公式或引用常量或公式的书签名称。函数AVERAGE、COUNT、MAX、MIN、PRODUCT和SUM还可以接受对表格单元格的引用作为参数。在表格单元格的上下文中，接受列表的函数还接受一个单独的参数，指定一组连续单元格的命名列表（[§17.16.3.5]）。函数名称不区分大小写，如果有的话，函数名称与其参数列表之间可以出现空白。
    
    支持的函数如下：
    
    | **函数**      | **描述**                                                                                                                                                                                                                                                |
    | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ABS(x)        | 返回x的绝对值。                                                                                                                                                                                                                                         |
    | AND(x,y)      | 如果逻辑表达式x和y都为真，则返回1；否则返回0。                                                                                                                                                                                                          |
    | AVERAGE(list) | 返回列表中项目的平均值。                                                                                                                                                                                                                                |
    | COUNT(list)   | 返回列表中的项目数。                                                                                                                                                                                                                                    |
    | DEFINED(x)    | 如果表达式x形式良好，则返回1；否则返回0。                                                                                                                                                                                                               |
    | FALSE         | 返回0。                                                                                                                                                                                                                                                 |
    | INT(x)        | 返回x的整数部分的值。                                                                                                                                                                                                                                   |
    | MAX(list)     | 返回列表中的最大值。                                                                                                                                                                                                                                    |
    | MIN(list)     | 返回列表中的最小值。                                                                                                                                                                                                                                    |
    | MOD(x,y)      | 返回值x - ny，其中n是某个整数，如果y不为零，则结果与x的符号相同且小于y的大小。如果y为零，将发出诊断。（y不必是整数。）[示例：<br/> MOD(21,5)的结果为1；<br/>MOD(21,-5)的结果为1；<br/>MOD(-21,5)的结果为-1；<br/>MOD(-21,-5)的结果为-1；<br/> 结束示例] |

=== "英文"
    
    A function is a predefined procedure that computes and returns a result. Functions defined below with a parameter list of list accept two or more arguments separated by commas (,) or semicolons (;). As to which separator is permitted, is defined by the document's listSeparator ([§17.15.1.56]) element. Arguments to functions can be constants, formulas, or bookmark names that refer to constants or formulas. The functions AVERAGE, COUNT, MAX, MIN, PRODUCT, and SUM can also accept references to table cells as arguments. In the context of a table cell, functions taking a list also accept a single argument that designates a named-list of contiguous cells ([§17.16.3.5]). Function names are not case-sensitive, and white space can occur between a function's name and its argument list, if any.
    
    The functions supported are as follows:
    
    | **Function**  | **Description**                                                                                                                                                                                                                                                                                                                                                                          |
    | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ABS(x)        | Returns the absolute value of x.                                                                                                                                                                                                                                                                                                                                                         |
    | AND(x,y)      | Returns 1 if the logical expressions x and y are both true; otherwise, it returns 0.                                                                                                                                                                                                                                                                                                     |
    | AVERAGE(list) | Returns the average value of the items in list.                                                                                                                                                                                                                                                                                                                                          |
    | COUNT(list)   | Returns the number of items in list.                                                                                                                                                                                                                                                                                                                                                     |
    | DEFINED(x)    | Returns 1 if the expression x is well formed; otherwise, it returns 0.                                                                                                                                                                                                                                                                                                                   |
    | FALSE         | Returns 0.                                                                                                                                                                                                                                                                                                                                                                               |
    | INT(x)        | Returns the value of the integer part of x.                                                                                                                                                                                                                                                                                                                                              |
    | MAX(list)     | Returns the largest value in list.                                                                                                                                                                                                                                                                                                                                                       |
    | MIN(list)     | Returns the smallest value in list.                                                                                                                                                                                                                                                                                                                                                      |
    | MOD(x,y)      | Returns the value x - ny, for some integer n such that, if y is nonzero, the result has the same sign as x and magnitude less than the magnitude of y. If y is zero, a diagnostic shall be issued. (y need not be a whole number.) [Example: <br/> MOD(21,5) results in 1 <br/> MOD(21,-5) results in 1  <br/> MOD(-21,5) results in -1<br/> MOD(-21,-5) results in -1<br/> end example] |

### 17.16.3.5 表格单元格引用

**Table cell references**

=== "中文"
    
    在 WordprocessingML 表格中，项目被组织为行和列，行和列交叉形成的框称为单元格。单元格有如 A1、A2、B1、B2 等名称，字母代表列，数字代表行。每个表格左上角的单元格命名为 A1。列的字母不区分大小写。
    
    一个单元格引用可以是以下之一：
    
    - 单元格的名称。
    - 以逗号分隔的单元格名称集合。
    - 一个单元格范围，其中使用冒号（:）分隔指定范围内的第一个和最后一个单元格，该范围具有连续的矩形形状。仅指定范围内第一个和最后一个单元格的行或列名称，会选择整行或整列，无论表格现在或将来有多少行和列。
    
    表格单元格中的表达式可以包含引用该表格中其他单元格的操作数。
    
    [示例：考虑一个具有三行（1、2 和 3）和两列（A 和 B）的表格：
    
    | -             | -                                                                    |
    | ------------- | -------------------------------------------------------------------- |
    | A1 + B1       | 返回单元格 A1 和 B1 的内容之和。                                     |
    | SUM(A1,B2,A3) | 返回单元格列表内容之和。                                             |
    | SUM(B1:B3)    | 返回单元格 B1 到 B3（含）的内容之和。                                |
    | SUM(B:B)      | 返回列 B 中所有单元格的内容之和（即使以后添加新行）。                |
    | SUM(A1:B2)    | 返回由 A1 和 B2 界定的矩形网格中所有（四个）单元格的内容之和（含）。 |
    | SUM(1:1,2:2)  | 返回第 1 行和第 2 行所有单元格的内容之和。                           |
    
    结束示例]
    
    在表格单元格中使用时，接受列表参数的函数可以有一个单独的参数：ABOVE（上方）、BELOW（下方）、LEFT（左方）或 RIGHT（右方），不区分大小写。此类列表分别指定该单元格上方、下方、左方或右方的所有单元格。然而，如果遇到内容为空或非数字的单元格，指定的范围将终止，但如果第一个单元格为空，它将被视为包含 0。[示例：给定以下表格：
    
    | -               | -             | -          |
    | --------------- | ------------- | ---------- |
    | 12              | =COUNT(BELOW) |            |
    |                 | 10            |            |
    | 2               | 20            | =SUM(LEFT) |
    | 3               | xxx           |            |
    | =AVERAGE(ABOVE) | 40            |            |
    
    AVERAGE(ABOVE) 的结果是 2.5，A4 和 A3 单元格的平均值；COUNT(BELOW) 的结果是 2，即 B2 和 B3；SUM(LEFT) 的结果是 22，即 B3 和 A3 的和。结束示例]
    
    在表格外部使用的表达式或一个表格单元格中的表达式可以通过对第二个表格做书签并使用表格名称限定该表格中的单元格名称，来引用第二个表格中的单元格，格式为：
    
    ```text
    (tableBookmarkName cellReference)
    ```
    
    [示例：假设 Table1 是一个 3x2 表格的书签，=SUM(Table1 A1:A3) 的结果是列 A 的单元格之和。结束示例]

=== "英文"
    
    Items in a WordprocessingML table are organized into rows and columns with the box formed by the intersection of a row and column being called a cell. Cells have names such as A1, A2, B1, B2, and so on, with the letter representing a column and the number representing a row. The cell at the top-left corner of each table is named A1. Column letters are not case-sensitive.

    A cell reference shall be one of the following:

    - The name of a cell.
    - A comma-separated set of cell names.
    - A cell range where a colon (:) is used to separate the first and last cells in a designated range of cells that has a contiguous rectangular shape. Specifying a row or column's name only as the first and last cell in a range, selects that whole row or column, regardless of the number of rows and columns the table has now or might have in the future.
    
    An expression inside a table's cell can have operands that are references to other cells in that table.
    
    [Example: Consider a table with three rows (1, 2, and 3) and two columns (A and B):
    
    | -             | -                                                                                                              |
    | ------------- | -------------------------------------------------------------------------------------------------------------- |
    | A1 + B1       | Returns the sum of the contents of cells A1 and B1.                                                            |
    | SUM(A1,B2,A3) | Returns the sum of the contents of the list of cells.                                                          |
    | SUM(B1:B3)    | Returns the sum of the contents of all cells between B1 and B3, inclusive.                                     |
    | SUM(B:B)      | Returns the sum of the contents of all cells in column B (even if new rows are added later).                   |
    | SUM(A1:B2)    | Returns the sum of the contents of all (four) cells in the rectangular grid delimited by A1 and B2, inclusive. |
    | SUM(1:1,2:2)  | Returns the sum of the contents of all cells in rows 1 and 2.                                                  |
    
    end example]


    When used in a table cell, the functions taking a list argument can have a single argument of ABOVE, BELOW,
    LEFT, or RIGHT, spelled in any case combination. Such lists designate, respectively, all the cells above, below, to
    the left of, or to the right of that cell. However, the designated range terminates if a cell with blank or non-
    numeric contents is reached, except that if the first cell is blank, it is treated as containing 0. [Example: Given the
    following table:
    
    | -               | -             | -          |
    | --------------- | ------------- | ---------- |
    | 12              | =COUNT(BELOW) |            |
    |                 | 10            |            |
    | 2               | 20            | =SUM(LEFT) |
    | 3               | xxx           |            |
    | =AVERAGE(ABOVE) | 40            |            |
    
    AVERAGE(ABOVE) results in 2.5, the average of cells A4 and A3; COUNT(BELOW) results in 2, B2 and B3; and SUM(LEFT) results in 22, the sum of B3 and A3. end example]
    
    An expression used outside a table or in a cell of one table can refer to cells in a second table by making a bookmark to that second table and qualifying cell names in that table by their table name using the form
    
    ```text
    (tableBookmarkName cellReference)
    ```
    
    [Example: Given that Table1 is a bookmark for a 3x2 table, =SUM(Table1 A1:A3) book results in the sum of column A's cells. end example]
    
## 17.16.4 字段格式

**Field formatting**

=== "中文"
    
    字段的结果具有格式，这可能是默认的，也可能是因为该字段包含了格式开关。字段格式化有三种类型：日期和时间（[§17.16.4.1]）、数字（[§17.16.4.2]）和通用（[§17.16.4.3]）。

=== "英文"

    The result of a field has a format, either by default or because that field contains a formatting-switch. There are three kinds of field formatting: date and time ([§17.16.4.1]), numeric ([§17.16.4.2]), and general ([§17.16.4.3]).

### 17.16.4.1 日期和时间格式

**Date and time formatting**

=== "中文"
    
    ```text
    date-and-time-formatting-switch=
        \@ switch-argument ;
    ```
    
    *日期和时间格式开关(date-and-time-formatting-switch)*指定日期或时间结果的格式。[注：此开关有时称为图片开关，因为它允许使用符号来表示字段结果的格式。结束注] 如果字段的结果不是日期或时间，此开关无效。
    
    如果没有*日期和时间格式开关(date-and-time-formatting-switch)*，则日期或时间结果以实现定义的方式格式化。
    
    日期和时间的*开关参数(switch-argument)*由一系列描述项组成。
    
    **日期格式描述项**
    
    （描述项 | 描述）
    
    - **aaa**
    
        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，以缩写形式格式化星期几或月份：
    
        - 如果 lang 元素是 ja-JP 或 ko-KR，则显示为相应的语言。
        - 对于所有其他 lang 元素值，将描述项显示为文本。
    
        多个此描述项的实例会创建重复内容。
    
    - **A**
    
        使用日文数字格式化日期为不带前导零的数字。
    
        多个此描述项的实例会创建重复内容。
    
    - **bb**
    
        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将年份格式化为两位数：
    
        - 如果 lang 元素是 zh-TW、zh-CN、zh-HK、zh-SG 或 zh-MO，则使用公历年 [ISO 8601]。
        - 对于所有其他 lang 元素值，使用泰国佛历年。
    
        此描述项可以修改其他描述项的行为。
    
        多个此描述项的实例会创建重复内容，除非模式包含“bbbb”描述项。此部分将按照“bbbb”描述项的描述格式化。
    
    - **bbbb**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将年份格式化为四位数：

        - 如果 lang 元素是 ZH-TW、zh-CN、zh-HK、zh-SG 或 zh-MO，则使用公历年 [ISO 8601]。
        - 对于所有其他 lang 元素值，使用泰国佛历年。

        此描述项可以修改其他描述项的行为。

        多个此描述项的实例会创建重复内容。

    - **BB**

        将年份格式化为两位数。

        默认使用公历 [ISO 8601]，但也响应 \s 和 \h 开关。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“BBBB”的组。每个组按照“BBBB”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“BB”的组使用该描述项的描述。

    - **BBBB**

        将年份格式化为四位数。

        默认使用公历 [ISO 8601]，但也响应 \s 和 \h 开关。

        多个此描述项的实例会根据“BB”描述项描述创建重复内容。

    - **d**

        将星期几或日期格式化为数字，对于个位数的日子不带前导零。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“dddd”的组。每个组按照“dddd”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“ddd”、“dd”和“d”的组使用各自描述项组的描述。
    
    - **dd**

        将星期几或日期格式化为带前导零的数字。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“d”描述项的描述创建重复内容。

    - **ddd**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几或月份格式化为缩写形式。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb、bbbb、ปปปป、ปป、ดดดด、ดดด、ดด、ด、วววว、ววว、วว 和 ว 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“d”描述项的描述创建重复内容。

    - **dddd**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几格式化为全名。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb、bbbb、ปปปป、ปป、ดดดด、ดดด、ดด、ด、วววว、ววว、วว 和 ว 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“d”描述项的描述创建重复内容。

    - **D**

        将星期几或日期格式化为不带前导零的数字。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“DDDD”的组。每个组按照“DDDD”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“DDD”、“DD”和“D”的组使用各自描述项组的描述。
    
    - **DD**

        将日期格式化为两位数字（对于个位数的日期带前导零）。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“D”描述项的描述创建重复内容。

    - **DDD**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几格式化为缩写形式。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb、ปปปป、ปป、ดดดด、ดดด、ดด、ด、วววว、ววว、วว 和 ว 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“D”描述项的描述创建重复内容。

    - **DDDD**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几格式化为全名。

        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb、bbbb、ปปปป、ปป、ดดดด、ดดด、ดด、ด、วววว、ววว、วว 和 ว 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据“D”描述项的描述创建重复内容。

    - **e**

        将日本天皇时代的年份格式化为不带前导零的数字。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“ee”的组。每个组按照“ee”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“e”的组使用该描述项的描述。

    - **ee**

        将日本天皇时代的年份格式化为带前导零的数字。

        多个此描述项的实例会根据“e”描述项的描述创建重复内容。
    
    - **E**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代：

        - 如果 lang 元素是 ja-JP，则显示日本天皇时代的年份（个位数的年份不带前导零）并使用相应语言。
        - 如果 lang 元素是 zh-TW，则显示台湾年份并使用相应语言。
        - 对于所有其他值，显示公历年 [ISO 8601] 为四位数，并使用 ja-JP 语言。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“EE”的组。每个组按照“EE”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“E”的组使用该描述项的描述。

    - **EE**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将公历年 [ISO 8601] 格式化为四位数：

        - 如果 lang 元素是 ja-JP、zh-TW、zh-CN、zh-HK、zh-SG 或 zh-MO，则使用相应的语言显示。
        - 对于所有其他 lang 元素值，使用 ja-JP 显示。

        多个此描述项的实例会根据“E”描述项的描述创建重复内容。

    - **g**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代：

        如果 lang 元素是 ko-KR 或 zh-TW，则不显示任何内容。

        对于所有其他 lang 元素值，以 en-US 显示日本天皇时代的缩写形式。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“ggg”的组。每个组按照“ggg”描述项的描述进行格式化。
        2. 从剩余的值中，重复步骤 1 对包含“gg”的组使用该描述项的描述。
        3. 从剩余的值中，重复步骤 1 对包含“g”的组使用该描述项的描述。

    - **gg**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代：

        - 如果 lang 元素是 ja-JP，则以相应语言显示日本天皇时代的缩写形式。
        - 如果 lang 元素是 ko-KR，则以相应语言显示韩国檀君纪元的全名。
        - 如果 lang 元素是 zh-TW，则以相应语言显示台湾纪元的全名。
        - 对于所有其他 lang 元素值，以 ja-JP 显示日本天皇时代的缩写形式。

        多个此描述项的实例会根据“g”描述项的描述创建重复内容。
    
    - **ggg**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代：

        - 如果 lang 元素是 ja-JP，则以相应语言显示日本天皇时代的全名。
        - 如果 lang 元素是 ko-KR，则以相应语言显示韩国檀君纪元的全名。
        - 如果 lang 元素是 zh-TW，则以相应语言显示台湾纪元的全名。
        - 对于所有其他 lang 元素值，以 ja-JP 显示日本天皇时代的全名。

        多个此描述项的实例会根据“g”描述项的描述创建重复内容。

    - **G**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代。

        - 如果 lang 元素是 ko-KR 或 zh-TW，则不显示任何内容。
        - 对于所有其他 lang 元素值，以 ja-JP 显示日本天皇时代的缩写形式。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“GG”的组。每个组按照“GG”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“G”的组使用该描述项的描述。

    - **GG**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言格式化时代。

        - 如果 lang 元素是 ko-KR，则以相应语言显示韩国檀君纪元的全名。
        - 如果 lang 元素是 zh-TW，则以相应语言显示台湾纪元的全名。
        - 对于所有其他 lang 元素值，以 ja-JP 显示日本天皇时代的全名。

        多个此描述项的实例会根据“G”描述项的描述创建重复内容。

    - **M**

        将月份格式化为不带前导零的数字。默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。

        多个此描述项的实例会根据以下规定创建重复内容：

        1. 从运行的文本方向开始，创建尽可能多的包含“MMMM”的组。每个组按照“MMMM”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“MMM”、“MM”和“M”的组使用各自描述项组的描述。
    
    - **MM**

        将月份格式化为两位数字（对于单个数字月份带有前导零）。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb 或 bbbb 描述项时（改为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据“M”描述项的描述创建重复内容。

    - **MMM**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将月份格式化为缩写形式。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, 和 ว 描述项时（改为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据“M”描述项的描述创建重复内容。

    - **MMMM**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将月份格式化为全名。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时以及使用 bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, 和 ว 描述项时（改为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据“M”描述项的描述创建重复内容。

    - **n**

        将日本天皇时代的年份格式化为无前导零的数字。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从运行的文本方向开始，创建尽可能多的包含“nn”的组。每个组按照“nn”描述项的描述进行格式化。
        2. 重复步骤 1 对包含“n”的组使用该描述项的描述。

    - **nn**

        将日本天皇时代的年份格式化为带前导零的数字。
        
        多个此描述项的实例会根据“n”描述项的描述创建重复内容。
    
    - **O**

        将月份格式化为日本数字形式的无前导零的数字。
        
        多个此描述项的实例会创建重复内容。

    - **w**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几格式化为缩写形式：
        
        - 如果 lang 元素是 ja-JP 或 ko-KR，则以相应语言显示。
        - 对于所有其他 lang 元素值，将描述项显示为文字文本。
        
        多个此描述项的实例会创建重复内容。

    - **W**

        根据包含字段指令的运行中的 lang 元素（[§17.3.2.20]）指定的语言，将星期几格式化为缩写形式：
        
        - 如果 lang 元素是 ja-JP、ko-KR、zh-TW、zh-CN、zh-HK、zh-SG 或 zh-MO，则以相应语言显示。
        - 对于所有其他 lang 元素值，将描述项显示为文字文本。
        
        多个此描述项的实例会创建重复内容。

    - **y**

        将年份格式化为两位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时会发生变化。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从运行的文本方向开始，创建尽可能多的包含“yyyy”的组。每个组按照“yyyy”描述项的描述进行格式化。
        2. 重复步骤 1，对包含“yy”和“y”的组分别使用各自描述项的描述。

    - **yy**

        将年份格式化为两位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时会发生变化。
        
        多个此描述项的实例会根据“y”描述项的描述创建重复内容。
    
    - **yyyy**

        将年份格式化为四位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关时会发生变化。
        
        多个此描述项的实例会根据“y”描述项的描述创建重复内容。

    - **Y**

        将年份格式化为两位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关以及 bb, bbbb, ปปปป 和 ปป 描述项时（转换为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从运行的文本方向开始，创建尽可能多的包含“YYYY”的组。每个组按照“YYYY”描述项的描述进行格式化。
        2. 重复步骤 1，对包含“YY”和“Y”的组分别使用各自描述项的描述。

    - **YY**

        将年份格式化为两位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关以及 bb, bbbb, ปปปป 和 ปป 描述项时（转换为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据“Y”描述项的描述创建重复内容。

    - **YYYY**

        将年份格式化为四位数字。
        
        默认使用公历 [ISO 8601]，但在存在 \s 和 \h 开关以及 bb, bbbb, ปปปป 和 ปป 描述项时（转换为泰国佛历年）会发生变化。
        
        多个此描述项的实例会根据“Y”描述项的描述创建重复内容。

    - **ว**

        将日期格式化为泰国数字形式的无前导零的数字。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从运行的文本方向开始，创建尽可能多的包含“วววว”的组。每个组按照“วววว”描述项的描述进行格式化。
        2. 重复步骤 1，对包含“ววว”、“วว”和“ว”的组分别使用各自描述项的描述。
    
    - **วว**

        将日期格式化为泰国数字形式的两位数（对于单个数字的日期，会有前导零）。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ว”描述项的描述创建重复内容。

    - **ววว**

        将泰国佛历的星期几以其缩写形式在泰语中显示。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ว”描述项的描述创建重复内容。

    - **วววว**

        将泰国佛历的星期几以其全名在泰语中显示。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ว”描述项的描述创建重复内容。

    - **ด**

        将泰国佛历的月份格式化为泰国数字形式的数字，对于单个数字的月份，不带有前导零。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从运行的文本方向开始，创建尽可能多的包含“ดดดด”的组。每个组按照“ดดดด”描述项的描述进行格式化。
        2. 对于“ดดด”、“ดด”和“ด”的组，重复步骤 1，使用各自描述项的描述。

    - **ดด**

        将泰国佛历的月份格式化为泰国数字形式的两位数（对于单个数字的月份，会有前导零）。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ด”描述项的描述创建重复内容。

    - **ดดด**

        将泰国佛历的月份以其缩写形式显示。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ด”描述项的描述创建重复内容。
    
    - **ดดดด**

        将泰国佛历的月份格式化为其全名。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ด”描述项的描述创建重复内容。

    - **ปป**

        使用泰国数字形式将格里高利历的年份格式化为两位数。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据以下规定创建重复内容：
        
        1. 从文本方向开始，创建尽可能多的包含“ปปปป”的组。每个组按照“ปปปป”描述项的描述进行格式化。
        2. 对于“ปป”的组，重复步骤1，使用该描述项的描述。

    - **ปปปป**

        使用泰国数字形式将格里高利历的年份（ISO 8601）格式化为四位数。
        
        此描述项可以修改其他描述项的行为。
        
        多个此描述项的实例会根据“ปป”描述项的描述创建重复内容。

    **其他格式化描述项**

    (描述项 | 描述)

    - **其他字符**

        在结果中包含指定的字符在该位置。【注：常用字符包括冒号（:）、连字符（-）、星号（*）、斜杠（/）和空格。结束注释】

    - **'文本'**
        
        在结果中包含文本。

    - **`编号项`**
        
        以阿拉伯数字包含前一项的编号，编号为标题或来自SEQ字段（[§17.16.5.56]）的结果。编号项应与SEQ字段中的标识符相同。
    
    [示例：在美国英语环境中，根据下面显示的日期和时间更新后，以下字段产生了以下结果：
    
    | -                                | -                         |
    | -------------------------------- | ------------------------- |
    | DATE \@ "M/d/yyyy"               | 1/3/2006                  |
    | DATE \@ "dddd, MMMM dd, yyyy"    | Tuesday, January 03, 2006 |
    | DATE \@ "MMMM d, yyyy"           | January 3, 2006           |
    | DATE \@ "M/d/yy"                 | 1/3/06                    |
    | DATE \@ "yyyy-MM-dd"             | 2006-01-03                |
    | DATE \@ "d-MMM-yy"               | 3-Jan-06                  |
    | DATE \@ "M.d.yyyy"               | 1.3.2006                  |
    | DATE \@ "MMM. d, yy"             | Jan. 3, 06                |
    | DATE \@ "d MMMM yyyy"            | 3 January 2006            |
    | DATE \@ "MMMM yy"                | January 06                |
    | DATE \@ "MMM-yy"                 | Jan-06                    |
    | DATE \@ "M/d/yyyy h:mm am/pm"    | 1/3/2006 5:28 PM          |
    | DATE \@ "M/d/yyyy h:mm:ss am/pm" | 1/3/2006 5:28:34 PM       |
    | DATE \@ "h:mm am/pm"             | 5:28 PM                   |
    | DATE \@ "h:mm:ss am/pm"          | 5:28:34 PM                |
    | DATE \@ "HH:mm"                  | 17:28                     |
    | DATE \@ "'Today is 'HH:mm:ss"    | Today is 17:28:34         |
    
    结束示例]

=== "英文"
    
    ```text
    date-and-time-formatting-switch=
        \@ switch-argument ;
    ```
    
    A *date-and-time-formatting-switch* specifies the format of a date or time result. [Note: This switch is sometimes called a picture switch because it allows the use of symbols to represent the format of the field result. end note] If the result of a field is not a date or time, this switch has no effect.
    
    If no *date-and-time-formatting-switch* is present, a date or time result is formatted in an implementation-defined manner.
    
    A date and time *switch-argument* is made up of a series of picture items.
    
    **Date Formatting Picture Items**
    
    (Picture Item | Description)
    
    - **aaa**
    
        Formats the day of the week or month in an abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
    
        - If the lang element is ja-JP or ko-KR, display in the corresponding language.
        - For all other lang element values, display picture item as text.
    
        Multiple instances of the picture item create repeated content.
    
    - **A**
    
        Formats the day of the month as a number without a leading zero for single-digit days in Japanese numerals.
    
        Multiple instances of the picture item create repeated content.
    
    - **bb**
    
        Formats the year as a 2-digit number according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
    
        - If the lang element is zh-TW, zh-CN, zh-HK, zh-SG, or zh-MO, use the Gregorian year [ISO 8601] .
        - For all other lang element values, use Thai Buddhist Era year 
    
        This picture item can modify the behaviour of other picture items.
    
        Multiple instances of the picture item create repeated content unless the pattern contains the “bbbb” picture item. Those portions are formatted following the description outlined for the “bbbb” picture item.
    
    - **bbbb**
    
        Formats the year as a 4-digit number according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ZH-TW, zh-CN, zh-HK, zh-SG, or zh-MO, use the Gregorian year [ISO 8601]
        - For all other lang element values, use Thai Buddhist Era year
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content.
    
    - **BB**
    
        Formats the year as a 2-digit number.
    
        Defaults to the Gregorian [ISO 8601] calendar, but also responds to the \s and \h switches.
        
        Multiple instances of the picture item create repeated content as specified by the following:
    
        3.&nbsp;Working from the text direction of the run, create as many groups as possible that contain “BBBB” in each group. Format each group using the description outlined for the “BBBB” picture item.
        4.&nbsp;Repeat step 1 for groups of “BB” using the description for that picture item.
    
    - **BBBB**
    
        Formats the year as a 4-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also responds to the \s and \h switches.
        
        Multiple instances of the picture item create repeated content as specified by the “BB” picture item description.
    
    - **d**
    
        Formats the day of the week or day of the month as a number without a leading zero for single-digit days.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “dddd” in each group. Format each group using the description outlined for the “dddd” picture item.
        2. Repeat step 1 for groups of “ddd”, “dd”, and “d” using the respective description for each picture item group.
    
    - **dd**
    
        Formats the day of the week or day of the month as a number with a leading zero0 for single-digit days.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “d” picture item description.
    
    - **ddd**
    
        Formats the day of the week or month in its abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “d” picture item description.
    
    - **dddd**
    
        Formats the day of the week as its full name according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “d” picture item description.
    
    - **D**
    
        Formats the day of the week or day of the month as a number without a leading zero for single-digit days.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “DDDD” in each group. Format each group using the description outlined for the “DDDD” picture item.
        2. Repeat step 1 for groups of “DDD”, “DD”, and “D” using the respective description for each picture item group.
    
    - **DD**
    
        Formats the day of the month as a two-digit number (with a leading zero for single-digit days).
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “D” picture item description.
    
    - **DDD**
    
        Formats the day of the week in an abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “D” picture item description.
    
    - **DDDD**
    
        Formats the day of the week as its full name according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “D” picture item description.
    
    - **e**
    
        Formats the Japanese Emperor Era era with no leading zero for single-digit years.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “ee” in each group. Format each group using the description outlined for the “ee” picture item.
        2. Repeat step 1 for groups of “e” using the description for that picture item.
    
    - **ee**
    
        Formats the Japanese Emperor Era era with a leading zero for single-digit years.
        
        Multiple instances of the picture item create repeated content as specified by the “e” picture item description.
    
    - **E**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ja-JP, display the Japanese Emperor Era era with no leading zero for single-digit years in the corresponding language.
        - If the lang element is zh-TW, display the Taiwanese year in the corresponding language.
        - For all other values, display the Gregorian year [ISO 8601] as a four-digit number using ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “EE” in each group. Format each group using the description outlined for the “EE” picture item.
        2. Repeat step 1 for groups of “E” using the description for that picture item.
    
    - **EE**
    
        Formats the Gregorian year [ISO 8601] as a four-digit number, according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        - If the lang element is ja-JP, zh-TW, zh-CN, zh-HK, zh-SG, or zh-MO display in the corresponding language.
        - For all other lang element values, display in ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the “E” picture item description.
    
    - **g**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        If the lang element is ko-KR or zh-TW, display nothing.
        
        For all other lang element values, display Japanese Emperor Era era as its abbreviated form in en-US.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “ggg” in each group. Format each group using the description outlined for the “ggg” picture item.
        2. From the remaining values, repeat step 1 for groups of “gg” using the description for that picture item.
        3. From the remaining values, repeat step 1 for groups of “g” using the description for that picture item.
    
    - **gg**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ja-JP, display the Japanese Emperor Era era as its abbreviated form in the corresponding language.
        - If the lang element is ko-KR, display the Korean Tangun era as its full name in the corresponding language.
        - If the lang element is zh-TW, display the Taiwanese era as its full name in the corresponding language.
        - For all other lang element values, display the Japanese Emperor Era era as its abbreviated form in ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the “g” picture item description.
    
    - **ggg**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ja-JP, display the Japanese Emperor Era era as its full name in the corresponding language.
        - If the lang element is ko-KR, display the Korean Tangun era as its full name in the corresponding language.
        - If the lang element is zh-TW, display the Taiwanese era as its full name in the corresponding language.
        - For all other lang element values, display the Japanese Emperor Era era as its full name in ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the “g” picture item description.
    
    - **G**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        - If the lang element is ko-KR or zh-TW, display nothing.
        - For all other lang element values, display the Japanese Emperor Era era as its abbreviated form in ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “GG” in each group. Format each group using the description outlined for the “GG” picture item.
        2. Repeat step 1 for groups of “G” using the description for that picture item.
    
    - **GG**
    
        Formats the era according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        - If the lang element is ko-KR, display the Korean Tangun era as its full name in the corresponding language.
        - If the lang element is zh-TW, display the Taiwanese era as its full name in the corresponding language.
        - For all other lang element values, display the Japanese Emperor Era era as its full name in ja-JP.
        
        Multiple instances of the picture item create repeated content as specified by the “G” picture item description.
    
    - **M**
    
        Formats the month as a number without a leading zero for single-digit months. Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “MMMM” in each group. Format each group using the description outlined for the “MMMM” picture item.
        2. Repeat step 1 for groups of “MMM”, “MM”, and “M” using the respective description for each picture item group.
    
    - **MM**
    
        Formats the month as a number with a leading zero for single-digit months.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb or bbbb picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “M” picture item description.
    
    - **MMM**
    
        Formats the month in its abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “M” picture item description.
    
    - **MMMM**
    
        Formats the month as its full name according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, ปป, ดดดด, ดดด, ดด, ด, วววว, ววว, วว, and ว picture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “M” picture item description.
    
    - **n**
    
        Formats the Japanese Emperor Era era with no leading zero for single-digit years.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “nn” in each group. Format each group using the description outlined for the “nn” picture item.
        2. Repeat step 1 for groups of “n” using the description for that picture item.
    
    - **nn**
    
        Formats the Japanese Emperor Era era with leading zero for single-digit years.
        
        Multiple instances of the picture item create repeated content as specified by the “n” picture item description.
    
    - **O**
    
        Formats the month as a number without a leading zero for single-digit months in Japanese numerals.
        
        Multiple instances of the picture item create repeated content.
    
    - **w**
    
        Formats the day of the week in an abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ja-JP or ko-KR, display in the corresponding language.
        - For all other lang element values, display picture item as literal text.
        
        Multiple instances of the picture item create repeated content.
    
    - **W**
    
        Formats the day of the week in an abbreviated form according to the language specified by the lang element ([§17.3.2.20]) on the run containing the field instructions:
        
        - If the lang element is ja-JP, ko-KR, zh-TW, zh-CN, zh-HK, zh-SG, or zh-MO, display in the corresponding language.
        - For all other lang element values, display the picture item as literal text.
        
        Multiple instances of the picture item create repeated content.
    
    - **y**
    
        Formats the year as a 2-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “yyyy” in each group. Format each group using the description outlined for the “yyyy” picture item.
        2. Repeat step 1 for groups of “yy” and “y” using the respective description for each picture item group.
    
    - **yy**
    
        Formats the year as a 2-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches.
        
        Multiple instances of the picture item create repeated content as specified by the “y” picture item description.
    
    - **yyyy**
    
        Formats the year as a 4-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches.
        
        Multiple instances of the picture item create repeated content as specified by the “y” picture item description.
    
    - **Y**
    
        Formats the year as a 2-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presenceof the \s and \h switches, and the bb, bbbb, ปปปป, and ปป picture item (to theThai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified bythe following:
        
        1. Working from the text direction of the run, create as many groups aspossible that contain “YYYY” in each group. Format each group using thedescription outlined for the “YYYY” picture item.
        2. Repeat step 1 for groups of “YY” and “Y” using the respective descriptionfor each picture item group.
    
    - **YY**
    
        Formats the year as a 2-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, and ปปpicture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “Y” picture item description.
    
    - **YYYY**
    
        Formats the year as a 4-digit number.
        
        Defaults to the Gregorian calendar [ISO 8601], but also changes in the presence of the \s and \h switches, and the bb, bbbb, ปปปป, and ปปpicture item (to the Thai Buddhist Era calendar).
        
        Multiple instances of the picture item create repeated content as specified by the “Y” picture item description.
    
    - **ว**
    
        Formats the day of the month as a number without a leading zero for single-digit days in Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “วววว” in each group. Format each group using the description outlined for the “วววว” picture item.
        2. Repeat step 1 for groups of “ววว”, “วว” and “ว” using the respective description for each picture item group.
    
    - **วว**
    
        Formats the day of the month as a two-digit number (with a leading zero for single-digit days) in Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ว” picture item description.
    
    - **ววว**
    
        Formats the Thai Buddhist Era day of the week in its abbreviated form in Thai.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ว” picture item description.
    
    - **วววว**
    
        Formats the Thai Buddhist Era day of the week as its full name in Thai.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ว” picture item description.
    
    - **ด**
    
        Formats the Thai Buddhist Era month as a number without a leading zero for single-digit months in Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “ดดดด” in each group. Format each group using the description outlined for the “ดดดด” picture item.
        2. Repeat step 1 for groups of “ดดด”, “ดด” and “ด” using the respective description for each picture item group.
    
    - **ดด**
    
        Formats the Thai Buddhist Era month as a two-digit number (with a leading zero for single-digit months) in Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ด” picture item description.
    
    - **ดดด**
    
        Formats the Thai Buddhist Era month in its abbreviated form.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ด” picture item description.
    
    - **ดดดด**
    
        Formats the Thai Buddhist Era month as its full name.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ด” picture item description.
    
    - **ปป**
    
        Formats the Gregorian year as a 2-digit number using Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the following:
        
        1. Working from the text direction of the run, create as many groups as possible that contain “ปปปป” in each group. Format each group using the description outlined for the “ปปปป” picture item.
        2. Repeat step 1 for groups of “ปป” using the description for that picture item.
    
    - **ปปปป**
    
        Formats the Gregorian year [ISO 8601] as a 4-digit number using Thai numerals.
        
        This picture item can modify the behaviour of other picture items.
        
        Multiple instances of the picture item create repeated content as specified by the “ปป” picture item description.
    
    
    **Miscellaneous Formatting Picture Items**
    
    (Picture Item | Description)
    
    - **Other character**
    
        Includes the specified character in the result at that position. [Note: Commonly used characters are colon (:), hyphen (-), asterisk (*), slash (/), and space. end note]
    
    - **'text'**
        
        Includes text in the result.
    
    - **`numbered-item`**
        
        Includes, in Arabic numerals, the number of the preceding item numbered as a caption or resulting from a SEQ field ([§17.16.5.56]). numbered-item shall be the same name as identifier in that SEQ field.
    
    [Example: When updated in a US-English context on the date and time shown below, the following fields produced these results:
    
    | -                                | -                         |
    | -------------------------------- | ------------------------- |
    | DATE \@ "M/d/yyyy"               | 1/3/2006                  |
    | DATE \@ "dddd, MMMM dd, yyyy"    | Tuesday, January 03, 2006 |
    | DATE \@ "MMMM d, yyyy"           | January 3, 2006           |
    | DATE \@ "M/d/yy"                 | 1/3/06                    |
    | DATE \@ "yyyy-MM-dd"             | 2006-01-03                |
    | DATE \@ "d-MMM-yy"               | 3-Jan-06                  |
    | DATE \@ "M.d.yyyy"               | 1.3.2006                  |
    | DATE \@ "MMM. d, yy"             | Jan. 3, 06                |
    | DATE \@ "d MMMM yyyy"            | 3 January 2006            |
    | DATE \@ "MMMM yy"                | January 06                |
    | DATE \@ "MMM-yy"                 | Jan-06                    |
    | DATE \@ "M/d/yyyy h:mm am/pm"    | 1/3/2006 5:28 PM          |
    | DATE \@ "M/d/yyyy h:mm:ss am/pm" | 1/3/2006 5:28:34 PM       |
    | DATE \@ "h:mm am/pm"             | 5:28 PM                   |
    | DATE \@ "h:mm:ss am/pm"          | 5:28:34 PM                |
    | DATE \@ "HH:mm"                  | 17:28                     |
    | DATE \@ "'Today is 'HH:mm:ss"    | Today is 17:28:34         |
    
    end example]


### 17.16.4.2 数字格式

**Numeric formatting**

=== "中文"
    
    ```text
    numeric-formatting-switch=
        \# switch-argument ;
    ```
    
    数值格式化开关指定数值结果的格式。如果字段的结果不是数字，则此开关不起作用。
    
    如果没有数值格式化开关，则数字结果将按照没有前导空格或尾部小数零的方式格式化。如果结果为负数，则会显示一个负号。如果结果是整数，则不会显示小数点。
    
    数值开关参数由一系列描述项组成。
    
    **数值格式化描述项**
    
    | 描述项                               | 描述                                                                                                                                                                                                         |
    | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | 0                                    | 指定在结果中显示的必需数字位置。如果结果在该位置不包括数字，则显示0。[示例：在美国英语环境中，=4+5 \\# 00.00 显示 "09.00"。]                                                                                 |
    | #                                    | 指定在结果中显示的必需数字位置。如果结果在该位置不包括数字，则显示一个空格。额外的小数位四舍五入。[示例：=9+6 \\# $### 显示 "$ 15"。]                                                                        |
    | x                                    | 删除 x 占位符左侧的数字。如果占位符位于小数点右侧，则结果会四舍五入到该位置。[示例：在美国英语环境中，=111053+111439 \\# x## 显示 "492"，=1/8 \\# 0.00x 显示 "0.125"，=3/4 \\# .x 显示 ".8"。]               |
    | .                                    | 指示小数点的位置。[示例：在美国英语环境中，=95.4 \# $###.00 显示 "$ 95.40"。] 显示的小数点字符是特定于区域设置的。                                                                                           |
    | ,                                    | 分隔三位数的组。[示例：在美国英语环境中，=2456800 \# $#,###,### 显示 "2,456,800"。] 显示的分隔符字符是特定于区域设置的。                                                                                     |
    | -                                    | 在负数结果前添加一个减号，或者如果结果为正数或零，则添加一个空格。[示例：=80-90 \\# -## 显示 "-10"，而 =90-80 \\# - ## 显示 " 80"。]                                                                         |
    | +                                    | 在正数结果前添加一个加号，在负数结果前添加一个减号，如果结果为0，则添加一个空格。[示例：=90-80 \\# +## 显示 "+10"，而 =80-90 \\# +## 显示 "-10"。]                                                           |
    | 其他字符                             | 在结果中的指定位置包含指定的字符。[示例：=33 \\# ##% 显示 "33%"。]                                                                                                                                           |
    | '文本'                               | 在结果中包含文本。[示例：在美国英语环境中，如果 Price 是 26.5 的书签，=Price*15% \\# "##0.00 '是销售税'" 显示 "$ 3.98 是销售税"。]                                                                           |
    | \`编号项\`                           | 使用阿拉伯数字，在前一项作为标题编号或由 SEQ 域（[§17.16.5.56]）产生的结果中包含编号。编号项应与 SEQ 域中的标识符相同。[示例：=SUM(A1:D4) \\# "##0.00 '是表的总和' \`table\`" 显示 "456.34 是表 2 的总和"。] |
    | 正数结果；</br>负数结果              | 为正数和负数结果指定不同的描述项集。零值使用正图片。[示例：=Sales95 \\# $#,##0.00;- $#,##0.00 显示该书签的正值使用 $#,##0.00，负值使用 -$#,##0.00。]                                                         |
    | 正数结果；</br>负数结果；</br>零结果 | 为正数、负数和零结果指定不同的描述项集。[示例：=Sales95 \\# $#,##0.00;-$#,##0.00;$0 显示该书签的正值使用 $#,##0.00，负值使用 - $#,##0.00，零值使用 $0。]                                                     |

=== "英文"
    
    ```text
    numeric-formatting-switch=
        \# switch-argument ;
    ```
    
    A numeric-formatting-switch specifies the format of a numeric result. If the result of a field is not a number, this switch has no effect.
    
    If no numeric-formatting-switch is present, a numeric result is formatted without leading spaces or trailing fractional zeros. If the result is negative, a leading minus sign is present. If the result is a whole number, no radix point is present.
    
    A numeric switch-argument is made up of a series of picture items.
    
    **Numeric Formatting Picture Items**
    
    | Picture Item                                               | Description                                                                                                                                                                                                                                                                                                                         |
    | ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | 0                                                          | Specifies the requisite numeric positions to display in the result. If the result doesnot include a digit in that position, 0 is displayed. [Example: In a US-Englishcontext, =4+5 \\# 00.00 displays "09.00". end example]                                                                                                         |
    | #                                                          | Specifies the requisite numeric positions to display in the result. If the result doesnot include a digit in that position, a space is displayed. Extra fractional digits arerounded off. [Example: =9+6 \\# $### displays "$ 15". end example]                                                                                     |
    | x                                                          | Drops digits to the left of the x placeholder. If the placeholder is to the right ofthe decimal point, the result is rounded to that place. [Example: In a US-Englishcontext, =111053+111439 \\# x## displays "492", =1/8 \\# 0.00x displays"0.125", and =3/4 \\# .x displays ".8". end example]                                    |
    | .                                                          | Indicates the radix-point position. [Example: In a US-English context, =95.4 \# $###.00 displays "$ 95.40. end example] The radix-point character displayed is locale-specific.                                                                                                                                                     |
    | ,                                                          | Separates groups of three digits. [Example: In a US-English context, =2456800 \# $#,###,### displays "2,456,800". end example] The separator character displayed is locale-specific.                                                                                                                                                |
    | -                                                          | Prepends a minus sign to a negative result, or prepends a space if the result is positive or 0. [Example: =80-90 \# -## displays "-10", while =90-80 \# - ## displays " 80". end example]                                                                                                                                           |
    | +                                                          | Prepends a plus sign to a positive result, a minus sign to a negative result, or aspace if the result is 0. [Example: =90-80 \# +## displays "+10", and =80-90 \# +## displays "-10". end example]                                                                                                                                  |
    | Other character                                            | Includes the specified character in the result at that position. [Example: =33 \# ##% displays "33%". end example]                                                                                                                                                                                                                  |
    | 'text'                                                     | Includes text in the result. [Example: In a US-English context, if Price is a bookmark for 26.5, =Price*15% \# "##0.00 'is the sales tax'" displays "$ 3.98 is the sales tax". end example]                                                                                                                                         |
    | \`numbered-item\`                                          | Includes, in Arabic numerals, the number of the preceding item numbered as a caption or resulting from a SEQ field ([§17.16.5.56]). numbered-item shall be the same name as identifier in that SEQ field. [Example: =SUM(A1:D4) \# "##0.00 'is the total of Table' `table`" displays "456.34 is the total of Table 2". end example] |
    | positive-result ; </br> negative-result                    | Specifiesdifferent sets of picture items for positive and negative results. A zero value uses the positive picture. [Example: =Sales95 \# $#,##0.00;- $#,##0.00 displays that bookmark's positive values using $#,##0.00, and it's negative values using -$#,##0.00. end example]                                                   |
    | positive-result ; </br> negative-result ;</br> zero-result | Specifies different sets of picture items for positive, negative, and zero results. [Example: =Sales95 \# $#,##0.00;-$#,##0.00;$0 displays that bookmark's positive values using $#,##0.00, it's negative values using - $#,##0.00, and its zero values using $0. end example]                                                      |
    


### 17.16.4.3 一般格式

**General formatting**

=== "中文"
    
    ```text
    general-formatting-switch=
        \* switch-argument ;
    ```
    
    通用格式化开关指定数值或文本结果的各种格式。如果字段的结果类型与指定的格式不对应，则此开关不起作用。
    
    开关参数由一系列描述项组成。

=== "英文"
    
    ```text
    general-formatting-switch=
        \* switch-argument ;
    ```
    
    A *general-formatting-switch* specifies a variety of formats for a numeric or text result. If the result type of a field
    does not correspond to the format specified, this switch has no effect.
    
    A *switch-argument* is made up of a series of picture items.

#### 17.16.4.3.1 一般格式 - 数值

**General formatting - Numeric Values**

=== "中文"
    
    以下开关参数适用于字段的字段结果为数值时。如果字段的结果类型不是数值，则这些开关不起作用。如果字段的结果根据字段说明的语言而变化，这些变化将内联标注：
    
    **通用格式化开关参数**
    
    （开关参数 | 描述）
    
    - **AIUEO**
    
        使用传统的 a-i-u-e-o 顺序以平假名字符格式化数值结果。[示例：1 \* AIUEO 的结果是ア。示例结束]
        
        对应于 aiueoFullWidth 的 ST_NumberFormat 枚举值。
    
    - **ALPHABETIC**
        
        将数值结果格式化为一个或多个大写拉丁字母字符的出现。值为 1 的结果为字母 A，值为 2 的结果为字母 B，依此类推，直到值为 26，其结果为字母 Z。对于大于 26 的值，从该值中重复减去 26，直到结果为 26 或更小。结果值确定要使用的字母，并且对于从原始值中减去 26 的每一次，都会重复相同的字母。[示例：=54 \* ALPHABETIC 的结果为“BBB”，因为从 54 中减去 26 两次，产生值 2，表示为字母 B。示例结束] 
        
        对应于 upperLetter 的 ST_NumberFormat 值。
    
    - **alphabetic**
        
        将数值结果格式化为一个或多个小写拉丁字母字符的出现。值为 1 的结果为字母 a，值为 2 的结果为字母 b，依此类推，直到值为 26，其结果为字母 z。对于大于 26 的值，从该值中重复减去 26，直到结果为 26 或更小。结果值确定要使用的字母，并且对于从原始值中减去 26 的每一次，都会重复相同的字母。[示例：=52 \* alphabetic 的结果为“zz”，因为从 52 中减去 26 一次，产生值 26，表示为字母 z。示例结束] 
        
        对应于 lowerLetter 的 ST_NumberFormat 枚举值。
    
    - **Arabic**

        使用阿拉伯基数数字格式化数值结果。[示例：对于页面 123，PAGE \* Arabic 的结果是 "123"。示例结束]

        对应于十进制的 ST_NumberFormat 枚举值。

    - **ARABICABJAD**

        使用升序阿贝加德数字格式化数值结果。[示例：12 \* ARABICABJAD 的结果为 ‫ل‬。示例结束]

        对应于阿拉伯阿贝加德的 ST_NumberFormat 枚举值。

    - **ARABICALPHA**

        使用阿拉伯字母字符格式化数值结果。[示例：12 \* ARABICABJAD 的结果为 ‫س‬。示例结束]

        对应于阿拉伯字母的 ST_NumberFormat 枚举值。

    - **阿拉伯破折号**

        使用阿拉伯基数数字格式化数值结果，前缀为 "- "，后缀为 " -"。[示例：对于页面 123，PAGE \* ArabicDash 的结果是 "- 123 -"。示例结束]

        对应于以破折号形式显示数字的 ST_NumberFormat 枚举值。

    - **BAHTTEXT**

        以以下形式格式化数值结果：

        - 如果值是整数，则使用泰国计数系统显示，并在结果后附加 บาทถ ้วน。
        - 如果值包含小数部分，则将小数部分四舍五入到两位小数，并以整数部分以泰国计数格式显示的形式显示，后接 บาท 和小数部分以泰国计数格式显示的形式，并以 สตางค์ 结尾。

        [示例：1 \* BAHTTEXT 的结果为 หนึ่งบาทถ้วน。示例结束]

        对应于泰文货币格式的 ST_NumberFormat 枚举值。

    - **CardText**

        将数值结果格式化为小写基数文本。[示例：对于页面 123，PAGE \* CardText 的结果是 "one hundred twenty-three"。示例结束]

        对应于基数文本的 ST_NumberFormat 枚举值。

    - **CHINESENUM1**

        使用适当计数系统中的升序数字格式化数值结果。[示例：10 \* CHINESENUM1 的结果为 十。示例结束]

        对应于中文计数（zh-CN）或台湾计数（zn-TW）的 ST_NumberFormat 枚举值。

    - **CHINESENUM2**

        使用适当法定格式中的顺序数字格式化数值结果。[示例：123 \* CHINESENUM2 的结果为 壹佰貳拾參。示例结束]

        对应于中文法定简体（zh-CN）或象形法定繁体（zh-TW）的 ST_NumberFormat 枚举值。

    - **CHINESENUM3**

        使用适当计数千制中的顺序数字格式化数值结果。[示例：10 \* CHINESENUM3 的结果为 一百二十 三。示例结束]

        对应于中文计数千（zh-CN）或台湾计数千（zh-TW）的 ST_NumberFormat 枚举值。

    - **CHOSUNG**

        使用韩文 Chosung 格式中的顺序数字格式化数值结果。[示例：1 \* CHOSUNG 的结果为 ㄱ。示例结束]

        对应于韩文 Chosung 的 ST_NumberFormat 枚举值。

    - **CIRCLENUM**

        使用圆圈内的十进制编号格式化数值结果，使用封闭的字母数字字符表示 1–20 范围内的数字。对于超出此范围的非负数，使用 ARABIC 格式化。[示例：12 \* CIRCLENUM 的结果为 ⑫。示例结束]

        对应于圆圈内的十进制（decimalEnclosedCircle）的 ST_NumberFormat 枚举值。

    - **DBCHAR**

        使用双字节阿拉伯编号格式化数值结果。[示例：123 \* DBCHAR 的结果为 １２３。示例结束]

        对应于全角十进制（decimalFullWidth）的 ST_NumberFormat 枚举值。

    - **DBNUM1**

        使用顺序数字形式的连续数字表意字符，使用适当的字符。[示例：12 \* DBNUM1 的结果为 一二。示例结束]

        对应于表意数字（ideographDigital）或韩文数字（koreanDigital）的 ST_NumberFormat 枚举值。
    
    - **DBNUM2**

        使用适当的计数系统格式化数值结果为顺序数字。[例如：12 \* DBNUM2 的结果是 十二。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 japaneseCounting (ja-JP) 或 koreanCounting (ko-KR)。

    - **DBNUM3**

        使用适当的法律计数系统格式化数值结果为顺序数字。[例如：12 \* DBNUM3 的结果是 壱拾弐。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 japaneseLegal (ja-JP) 或 koreanLegal (ko-KR)。

    - **DBNUM4**

        使用适当的数字计数系统格式化数值结果为顺序数字。[例如：12 \* DBNUM4 的结果是 一二。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 japaneseDigitalTenThousand (ja-JP) 或 koreanDigital2 (ko-KR) 或 taiwaneseDigital (zh-TW)。

    - **DollarText**

        按以下格式格式化数值结果：
        
        *整数部分转换为基数文本* and *nn/100*
        
        小数部分四舍五入到小数点后两位，nn，使用阿拉伯基数数字格式化。[例如：=1234.567 \* DollarText 的结果是 "one thousand two hundred thirty-four and 57/100"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 dollarText。

    - **GANADA**

        使用韩文“加那大”格式格式化数值结果为顺序数字。[例如：12 \* GANADA 的结果是 타。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ganada。

    - **GB1**

        使用小数编号后跟一个句号，并使用括起来的字母数字字符格式化数值结果。[例如：12 \* GB1 的结果是 ⒓。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 decimalEnclosedFullstop。
    
    - **GB2**
    
        使用括号内的小数编号格式化数值结果，使用括起来的字母数字字符。[例如：12 \* GB2 的结果是 ⑿。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 decimalEnclosedParen。
    
    - **GB3**
    
        使用圆圈内的小数编号格式化数值结果，使用括起来的字母数字字符。一旦指定序列达到11，数字可以替换为非括号内的等效字符。[例如：12 \* GB3 的结果是 12。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 decimalEnclosedCircleChinese。
    
    - **GB4**
    
        使用圆圈内的小数编号格式化数值结果，使用括起来的字母数字字符。一旦指定序列达到11，数字可以替换为非括号内的等效字符。[例如：12 \* GB4 的结果是 12。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ideographEnclosedCircle。
    
    - **HEBREW1**
    
        使用希伯来数字格式化数值结果。[例如：123 \* HEBREW1 的结果是 ‫קכג‬。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hebrew1。
    
    - **HEBREW2**
    
        使用希伯来字母表格式化数值结果。[例如：123 \* HEBREW2 的结果是 ‫תתתתתמ‬。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hebrew2。
    
    - **Hex**
    
        使用大写十六进制数字格式化数值结果。[例如：对于页码355，PAGE \* Hex 的结果是 "FF"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hex。
    
    - **HINDIARABIC**
    
        使用印地数字格式化数值结果。[例如：123 \* HINDIARABIC 的结果是 १२३。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hindiNumbers。
    
    - **HINDICARDTEXT**
    
        使用印地计数系统的顺序数字格式化数值结果。[例如：123 \* HINDICARDTEXT 的结果是 एक सौ तेईस。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hindiCounting。
    
    - **HINDILETTER1**
    
        使用印地语元音格式化数值结果。[例如：123 \* HINDILETTER1 的结果是 ठठठठ。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hindiVowels。
    
    - **HINDILETTER2**
    
        使用印地语辅音格式化数值结果。[例如：123 \* HINDILETTER2 的结果是 ओओओओओओओ。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 hindiConsonants。
    
    - **IROHA**
    
        使用日文“いろは”格式化数值结果。[例如：12 \* IROHA 的结果是 オ。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 irohaFullWidth。
    
    - **KANJINUM1**
    
        使用日式风格并使用适当的计数系统格式化数值结果。[例如：12 \* KANJINUM1 的结果是 一二。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 koreanDigital (ko-KR)、ideographDigital (ja-JP)、chineseCounting (zh-CN) 或 taiwaneseCounting (zh-TW)。
    
    - **KANJINUM2**
    
        使用适当的计数系统格式化数值结果。[例如：12 \* KANJINUM2 的结果是 十二。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 koreanCounting (ko-KR)、chineseCountingThousand (ja-JP)、chineseLegalSimplified (zh-CN) 或 ideographLegalTraditional (zh-TW)。
    
    - **KANJINUM3**
    
        使用适当的计数系统格式化数值结果。[例如：12 \* KANJINUM3 的结果是 壱拾弐。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 koreanLegal (ko-KR)、japaneseLegal (ja-JP)、chineseCountingThousand (zh-CN) 或 taiwaneseCountingThousand (zh-TW)。
    
    - **Ordinal**
    
        使用小写序数阿拉伯数字格式化数值结果。[例如：=32 \* Ordinal 的结果是 "32nd"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ordinal。

    - **OrdText**

        将数值结果格式化为小写序数文本。除用于四舍五入整数部分外，小数部分不使用。[例如：=1234.567 \* OrdText 的结果是 "one thousand two hundred thirty-fifth"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ordinalText。

    - **Roman**

        使用大写罗马数字格式化数值结果。[例如：对于页码123，PAGE \* Roman 的结果是 "CXXIII"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 upperRoman。

    - **roman**

        使用小写罗马数字格式化数值结果。[例如：对于页码123，PAGE \* roman 的结果是 "cxxiii"。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 lowerRoman。

    - **SBCHAR**

        使用单字节阿拉伯数字格式化数值结果。[例如：123 \* SBCHAR 的结果是 123。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 decimalHalfWidth。

    - **THAIARABIC**

        使用泰国数字格式化数值结果。[例如：123 \* THAIARABIC 的结果是 ๑๒๓。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 thaiNumbers。

    - **THAICARDTEXT**

        使用泰国计数系统的顺序数字格式化数值结果。[例如：123 \* THAICARDTEXT 的结果是 หนึ่งร้อยยีสิบสาม。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 thaiCounting。

    - **THAILETTER**

        使用泰国字母格式化数值结果。[例如：30 \* THAILETTER 的结果是 ฮฮฮม。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 thaiLetters。

    - **VIETCARDTEXT**

        使用越南数字格式化数值结果。[例如：12 \* VIETCARDTEXT 的结果是 mười hai。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 vietnameseCounting。
    
    - **ZODIAC1**
    
        使用顺序数字传统表意文字格式化数值结果。[例如：1 \* ZODIAC1 的结果是 甲。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ideographTraditional。
    
    - **ZODIAC2**
    
        使用顺序生肖表意文字格式化数值结果。[例如：1 \* ZODIAC2 的结果是 子。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ideographZodiac。
    
    - **ZODIAC3**
    
        使用顺序传统生肖表意文字格式化数值结果。[例如：1 \* ZODIAC3 的结果是 甲子。结束示例]
        
        对应于 ST_NumberFormat 枚举值的 ideographZodiacTraditional。

=== "英文"
    
    The following switch-arguments apply to fields whose field result is a numeric value. If the result type of the field is not numeric, then these switches have no effect. If the field result varies based on the language of the field instructions, those variations are noted inline:
    
    **General Formatting Switch Arguments**
    
    (Switch Argument | Description)
    
    - **AIUEO**
    
        Formats a numeric result using hiragana characters in the traditional a-i-u-e-o order. [Example: 1 \* AIUEO results in ア. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of aiueoFullWidth.
    
    - **ALPHABETIC**
        
        Formats a numeric result as one or more occurrences of an uppercase alphabetic Latin character. Value 1 results in the letter A, value 2 results in the letter B, and so on up to value 26, which results in the letter Z. For values greater than 26, 26 is repeatedly subtracted from the value until the result is 26 or less. The result value determines which letter to use, and the same letter is repeated for each time 26 was subtracted from the original value. [Example: =54 \* ALPHABETIC results in "BBB" as subtracting 26 from 54 two times, producesthe value 2, which is represented by the letter B. end example] 
        
        Corresponds to an ST_NumberFormat value of upperLetter.
    
    - **alphabetic**
        
        Formats a numeric result as one or more occurrences of an lowercase alphabetic Latin character. Value 1 results in the letter a, value 2 results in the letter b, and so on up to value 26, which results in the letter z. For values greater than 26, 26 is repeatedly subtracted from the value until the result is 26 or less. The result value determines which letter to use, and the same letter is repeated for each time 26 was subtracted from the original value. [Example: =52 \* alphabetic results in "zz" as subtracting 26 from 52 one time, produces the value 26, which is represented by the letter z.. end example] 
        
        Corresponds to an ST_NumberFormat enumeration value of lowerLetter.
    
    - **Arabic**
    
        Formats a numeric result using Arabic cardinal numerals. [Example: For page 123, PAGE \* Arabic results in "123". end example] 
        
        Corresponds to an ST_NumberFormat enumeration value of decimal.
    
    - **ARABICABJAD**
    
        Formats a numeric result using ascending Abjad numerals. [Example: 12 \* ARABICABJAD results in ‫ل‬. end example] 
        
        Corresponds to an ST_NumberFormat enumeration value of arabicAbjad.
    
    - **ARABICALPHA**
    
        Formats a numeric result using characters in the Arabic alphabet. [Example: 12 \* ARABICABJAD results in ‫س‬. end example] 
        
        Corresponds to an ST_NumberFormat enumeration value of arabicAlpha.
    
    - **ArabicDash**
    
        Formats a numeric result using Arabic cardinal numerals, with a prefix of "- " and a suffix of " -". [Example: For page 123, PAGE \* ArabicDash results in "- 123 -". end example] 
        
        Corresponds to an ST_NumberFormat enumeration value of numberInDash.
    
    - **BAHTTEXT**
    
        Formats a numeric result in the following form:
    
        - If the value is an integer, it is displayed using the . Thai counting system, with บาทถ ้วน appended to the result.
        - If the value includes a fractional value, the fractional part is rounded to two decimal places, and the resulting value is displayed in the form integer-part-in-Thai-counting format บาท fractional-part-in-Thai-counting format สตางค์.
    
        [Example: 1 \* BAHTTEXT results in หนึ่งบาทถ้วน. end example] 
    
        Corresponds to an ST_NumberFormat enumeration value of bahtText.
    
    - **CardText**
    
        Formats a numeric result as lowercase cardinal text. [Example: For page 123, PAGE \* CardText results in "one hundred twenty-three". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of cardinalText.
    
    - **CHINESENUM1**
    
        Formats a numeric result using ascending numbers from the appropriate counting system. [Example: 10 \* CHINESENUM1 results in 十. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of chineseCounting (zh-CN) or taiwaneseCounting (zn-TW).
    
    - **CHINESENUM2**
    
        Formats a numeric result using sequential numbers from the appropriate legal format. [Example: 123 \* CHINESENUM2 results in 壹佰貳拾參. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of chineseLegalSimplified (zh-CN) or ideographLegalTraditional (zh-TW).
    
    - **CHINESENUM3**
    
        Formats a numeric result using sequential numbers from the appropriate counting thousand system. [Example: 10 \* CHINESENUM3 results in 一百二十 三. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of chineseCountingThousand (zh-CN) or taiwaneseCountingThousand (zh-TW).
    
    - **CHOSUNG**
    
        Formats a numeric result using sequential numbers from the Korean Chosung format. [Example: 1 \* CHOSUNG results in ㄱ. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of chosung.
    
    - **CIRCLENUM**
    
        Formats a numeric result using decimal numbering enclosed in a circle, using the enclosed alphanumeric glyph character for numbers in the range 1–20. For non- negative numbers outside this range, formats them as with ARABIC. [Example: 12 \* CIRCLENUM results in ⑫. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalEnclosedCircle.
    
    - **DBCHAR**
    
        Formats a numeric result using double-byte Arabic numbering. [Example: 123 \* DBCHAR results in １２３. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalFullWidth.
    
    - **DBNUM1**
    
        Formats a numeric result using sequential digital ideographs, using the appropriate character. [Example: 12 \* DBNUM1 results in 一二. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ideographDigital (ja-JP) or koreanDigital (ko-KR).
    
    - **DBNUM2**
    
        Formats a numeric result using sequential numbers from the appropriatecounting system. [Example: 12 \* DBNUM2 results in 十二. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of japaneseCounting (ja-JP) or koreanCounting (ko-KR).
    
    - **DBNUM3**
    
        Formats a numeric result using sequential numbers from the appropriate legal counting system. [Example: 12 \* DBNUM3 results in 壱拾弐. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of japaneseLegal (ja-JP) or koreanLegal (ko-KR).
    
    - **DBNUM4**
    
        Formats a numeric result using sequential numbers from the appropriate digital counting system. [Example: 12 \* DBNUM4 results in 一二. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of japaneseDigitalTenThousand (ja-JP) or koreanDigital2 (ko-KR) or taiwaneseDigital (zh-TW).
    
    - **DollarText**
    
        Formats a numeric result in the following form:
        
        *integer-part-as-cardinal-text* and *nn/100*
        
        The fractional part is rounded to two decimal places, nn, and is formatted using Arabic cardinal numerals. [Example: =1234.567 \*  ollarText results in "one thousand two hundred thirty-four and 57/100". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of dollarText.
    
    - **GANADA**
    
        Formats a numeric result using sequential numbers from the Korean Ganada format. [Example: 12 \* GANADA results in 타. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ganada.
    
    - **GB1**
    
        Formats a numeric result using decimal numbering followed by a period, using the enclosed alphanumeric glyph character. [Example: 12 \* GB1 results in ⒓. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalEnclosedFullstop.
    
    - **GB2**
    
        Formats a numeric result using decimal numbering enclosed in parenthesis, using the enclosed alphanumeric glyph character. [Example: 12 \* GB2 results in ⑿. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalEnclosedParen.
    
    - **GB3**
    
        Formats a numeric result using decimal numbering enclosed in a circle, using the enclosed alphanumeric glyph character. Once the specified sequence reaches 11, the numbers can be replaced with non-enclosed equivalents. [Example: 12 \* GB3 results in 12. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalEnclosedCircleChinese.
    
    - **GB4**
    
        Formats a numeric result using decimal numbering enclosed in a circle, using the enclosed alphanumeric glyph character. Once the specified sequence reaches 11, the numbers can be replaced with non-enclosed equivalents. [Example: 12 \* GB4 results in 12. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ideographEnclosedCircle.
    
    - **HEBREW1**
    
        Formats a numeric result using Hebrew numerals. [Example: 123 \* HEBREW1 results in ‫קכג‬. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hebrew1.
    
    - **HEBREW2**
    
        Formats a numeric result using the Hebrew alphabet. [Example: 123 \* HEBREW2 results in ‫תתתתתמ‬. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hebrew2.
    
    - **Hex**
    
        Formats the numeric result using uppercase hexadecimal digits. [Example: For page 355, PAGE \* Hex results in "FF". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hex.
    
    - **HINDIARABIC**
    
        Formats a numeric result using Hindi numbers. [Example: 123 \* HINDIARABIC results in १२३. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hindiNumbers.
    
    - **HINDICARDTEXT**
    
        Formats a numeric result using sequential numbers from the Hindi counting system. [Example: 123 \* HINDICARDTEXT results in एक सौ तेईस. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hindiCounting.
    
    - **HINDILETTER1**
    
        Formats a numeric result using Hindi vowels. [Example: 123 \* HINDILETTER1 results in ठठठठ. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hindiVowels.
    
    - **HINDILETTER2**
    
        Formats a numeric result using Hindi consonants. [Example: 123 \* HINDILETTER2 results in ओओओओओओओ. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of hindiConsonants.
    
    - **IROHA**
    
        Formats a numeric result using the Japanese iroha. [Example: 12 \* IROHA results in オ. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of irohaFullWidth.
    
    - **KANJINUM1**
    
        Formats a numeric result using a Japanese style using the appropriate counting system. [Example: 12 \* KANJINUM1 results in 一二. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of koreanDigital (ko-KR), ideographDigital (ja-JP), chineseCounting (zh-CN), or taiwaneseCounting (zh-TW).
    
    - **KANJINUM2**
    
        Formats a numeric result using the appropriatecounting system. [Example: 12 \* KANJINUM2 results in 十二. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of koreanCounting (ko-KR), chineseCountingThousand (ja-JP), chineseLegalSimplified (zh-CN), or ideographLegalTraditional (zh-TW).
    
    - **KANJINUM3**
    
        Formats a numeric result using the appropriatecounting system. [Example: 12 \* KANJINUM3 results in 壱拾弐. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of koreanLegal (ko-KR) or japaneseLegal (ja-JP) or chineseCountingThousand (zh-CN) or taiwaneseCountingThousand (zh-TW).
        
        OrdinalFormats a numeric result using lowercase ordinal Arabic numerals. [Example: =32 \* Ordinal results in "32nd". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ordinal.
    
    - **OrdText**
    
        Formats a numeric result as lowercase ordinal text. Apart from being used to round off the whole number part, the fractional part is not used. [Example: =1234.567 \* OrdText results in "one thousand two hundred thirty-fifth". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ordinalText.
    
    - **Roman**
    
        Formats a numeric result using uppercase Roman numerals. [Example: For page 123, PAGE \* Roman results in "CXXIII". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of upperRoman.
    
    - **roman**
    
        Formats a numeric result using lowercase Roman numerals. [Example: For page 123, PAGE \* roman results in "cxxiii". end example]
        
        Corresponds to an ST_NumberFormat enumeration value of lowerRoman.
    
    - **SBCHAR**
    
        Formats a numeric result using single-byte Arabic numbering. [Example: 123 \* SBCHAR results in 123. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of decimalHalfWidth.
    
    - **THAIARABIC**
    
        Formats a numeric result using Thai numbers. [Example: 123 \* THAIARABIC results in ๑๒๓. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of thaiNumbers.
    
    - **THAICARDTEXT**
    
        Formats a numeric result using sequential numbers from the Thai counting system. [Example: 123 \* THAICARDTEXT results in หนึ่งร้อยยีส่ บิ สาม. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of thaiCounting.
    
    - **THAILETTER**
    
        Formats a numeric result using Thai letters. [Example: 30 \* THAILETTER results in ฮฮฮม. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of thaiLetters.
    
    - **VIETCARDTEXT**
    
        Formats a numeric result using Vietnamese numerals. [Example: 12 \* VIETCARDTEXT results in mười hai. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of vietnameseCounting.
    
    - **ZODIAC1**
    
        Formats a numeric result using sequential numerical traditional ideographs. [Example: 1 \* ZODIAC1 results in 甲. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ideographTraditional.
    
    - **ZODIAC2**
    
        Formats a numeric result using sequential zodiac ideographs. [Example: 1 \* ZODIAC2 results in 子. end example]
         
        Corresponds to an ST_NumberFormat enumeration value of ideographZodiac.
    
    - **ZODIAC3**
    
        Formats a numeric result using sequential traditional zodiac ideographs. [Example: 1 \* ZODIAC3 results in 甲子. end example]
        
        Corresponds to an ST_NumberFormat enumeration value of ideographZodiacTraditional.

#### 17.16.4.3.2 一般格式 - 字符串值

**General formatting - String Values**

=== "中文"
    
    以下的切换参数适用于其字段结果为字符串值的字段：
    
    **通用格式化切换参数**
    
    （切换参数 | 描述）
    
    - **Caps**
    
        将每个单词的首字母大写。[例如：USERNAME "mary smith" \* Caps 的结果是 "Mary Smith"，而 USERNAME "marysmith" \* Caps 的结果是 "Marysmith"。结束示例]
    
    - **First**
        
        将第一个单词的首字母大写。[例如：USERNAME "mary smith" \* First 的结果是 "Mary smith"。结束示例]
    
    - **Lower**
        
        所有字母均为小写。[例如：USERNAME "Mary Smith" \* Lower 的结果是 "mary smith"。结束示例]
    
    - **Upper**
        
        所有字母均为大写。[例如：USERNAME "Mary Smith" \* Upper 的结果是 "MARY SMITH"。结束示例]

=== "英文"

    The following switch-arguments apply to fields whose field result is a string value:

    **General Formatting Switch Arguments**

    (Switch Argument | Description)

    - **Caps**
    
        Capitalizes the first letter of each word. [Example: USERNAME "mary smith" \* Caps results in "Mary Smith", whereas USERNAME "marysmith" \* Caps results in "Marysmith". end example]

    - **First**
        
        CapCapitalizes the first letter of the first word. [Example: USERNAME "mary smith" \* FirstCap results in "Mary smith". end example]

    - **Lower**
        
        All letters are lowercase. [Example: USERNAME "Mary Smith" \* Lower results in "mary smith". end example]

    - **Upper**
        
        All letters are uppercase. [Example: USERNAME "Mary Smith" \* Upper results in "MARY SMITH". end example]

#### 17.16.4.3.3 一般格式 - 字段结果格式

**General formatting - Field Result Formatting**

=== "中文"
    
    以下的切换参数适用于任何字段结果，并向应用程序提供在字段更新后应应用于字段结果的格式说明。如[§17.16]中所讨论的，何时执行字段更新不在ECMA-376的范围内。
    
    通用格式化切换参数 CHARFORMAT 是一条指令，指定在字段更新后应用于字段结果的格式。如果存在此切换参数，则包含 fldChar 元素且其 fldCharType 属性值为 begin 的第一个 instrText 元素的运行格式将应用于字段结果中的所有运行，每当生成新的字段结果时都会如此。[例如：在美国英语环境下，2006年1月4日，字段 DATE \* CHARFORMAT 的结果是 "1/4/2006"。然而，如果字段指令内的第一个运行（包含 DATE 中的 D）是粗体，则字段 DATE \* CHARFORMAT 的结果是 "1/4/2006"。如果该 D 是斜体，字段 DATE \* CHARFORMAT 的结果是 "1/4/2006"。如果该 D 是粗体、下划线并且是红色，字段 DATE \* CHARFORMAT 的结果是 "**1/4/2006**"。
    
    以下是粗体、下划线、红色情况的 XML：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> </w:instrText>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:instrText>D</w:instrText>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">ATE </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>1/4/2006</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    然后使用 CHARFORMAT 切换参数会导致新的字段结果重用字段指令中第一个运行的格式，如下所示：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> </w:instrText>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:instrText>D</w:instrText>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">ATE /* CHARFORMAT</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>1/4/2006</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    [结束示例]
    
    如果字段的字段类型名称的第一个运行中直接指定的格式与通用格式化切换参数冲突，则忽略通用格式化切换参数。[例如：如果第一个运行设置为小型大写字母且同时使用了切换参数 \* Lower，则该切换参数被忽略。结束示例]
    
    通用格式化切换参数 MERGEFORMAT 用于指定在字段更新后应用于字段结果的格式指令。如果存在此切换参数，它指示执行字段更新的应用程序在生成新字段结果时应保留现有字段结果的格式，并通过以下逻辑应用：
    
    - 删除当前字段结果中的所有文本（保留段落和运行结构）。
    - 将新字段结果文本插入现有的运行/段落结构中。
    - 如果新文本未填满现有结构，则删除多余的运行/段落。
    - 如果新文本溢出现有结构，则根据需要添加额外的运行/段落。
    
    [例如：考虑以下字段：
    
        TIME \@ "HH:mm:ss" \* MERGEFORMAT
    
    当它更新时，结果可能是 12:22:27。例如，如果显示的字段结果中的秒部分在原始 WordprocessingML 中通过直接格式设置被下划线，如 12:22:27，则该字段在下次更新时，会保留秒部分的下划线格式。
    
    如果为该字段生成的原始 XML 是：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> TIME \@ "HH:mm:ss" \* MERGEFORMAT
        </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>17:02:</w:t>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>32</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    那么使用 MERGEFORMAT 切换参数会导致新字段结果重用该结构，如下所示：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText>TIME \@ "HH:mm:ss" \* MERGEFORMAT</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>12:22:</w:t>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>27</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    而省略该参数则指示应用程序可以用单个新的运行来替换它，如下所示：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText>TIME \@ "HH:mm:ss"</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>12:22:27</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    结束示例]

=== "英文"
    
    The following switch-arguments apply to any field result, and provide directions to applications regarding the formatting which should be applied to a field result after a field update has been performed. As discussed in [§17.16], as to when a field update is performed is outside the scope of ECMA-376.
    
    The general formatting switch argument CHARFORMAT is an instruction that specifies formatting intended for application to the field result after a field update. If this switch is present, the formatting of the run containing the first instrText element after the fldChar element with a fldCharType attribute value of begin is applied to all runs in the field result whenever a new field result is generated. [Example: In a US-English context, on January 4, 2006, the field DATE \* CHARFORMAT results in "1/4/2006". However, if the first run within the field instructions (containing the D in DATE) is bold, the field DATE \* CHARFORMAT results in "1/4/2006". If that D is italic, the field DATE \* CHARFORMAT results in "1/4/2006". If that D is bold, underlined, and red, the field DATE \* CHARFORMAT results in "**1/4/2006**".
    
    The XML for the bold, underlined, red case is as follows:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> </w:instrText>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:instrText>D</w:instrText>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">ATE </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>1/4/2006</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    Then use of the CHARFORMAT switch would cause the new field result to reuse the formatting on the first run in the field instructions, like this:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> </w:instrText>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:instrText>D</w:instrText>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve">ATE /* CHARFORMAT</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:b/>
            <w:color w:val="ED1C24"/>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>1/4/2006</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    end example]
    
    If a format specified directly in the first run of a field's field-type name conflicts with a general formatting switch, the general formatting switch is ignored. [Example: If the first run is set in small caps and the switch \* Lower is also used, that switch is ignored. end example]
    
    The general formatting switch argument MERGEFORMAT is used to specify an instruction regarding the formatting which is applied to the field result after a field update. If this switch is present, it specifies that applications that perform field updates should preserve the formatting of the existing field result when a new field result is generated, by applying the following logic:
    
    
    
    - Delete all text from the current field result (leaving the paragraph and run structure intact).
    - Insert the new field result text into the existing run/paragraph structure.
    
    - If the new text does not fill the existing structure, delete the superfluous runs/paragraphs.
    - If the new text overflows the existing structure, add additional runs/paragraphs as needed.
    
    [Example: Consider the following field:
    
        TIME \@ "HH:mm:ss" \* MERGEFORMAT
    
    When it is updated, the result might be 12:22:27, for example. If the seconds part of the displayed field result was underlined by the use of direct formatting within the original WordprocessingML, as in 12:22:27, when that field is next updated, the seconds underlining is preserved.
    
    If the original XML generated for this field is:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText xml:space="preserve"> TIME \@ "HH:mm:ss" \* MERGEFORMAT
        </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>17:02:</w:t>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>32</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    then use of the MERGEFORMAT switch would cause the new field result to reuse that structure, like this:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText>TIME \@ "HH:mm:ss" \* MERGEFORMAT</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r …>
        <w:t>12:22:</w:t>
    </w:r>
    <w:r …>
        <w:rPr>
            <w:u w:val="single"/>
        </w:rPr>
        <w:t>27</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    and omitting it would direct an application that it could replace it with a single new run, like this:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin"/>
    </w:r>
    <w:r>
        <w:instrText>TIME \@ "HH:mm:ss"</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>12:22:27</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    end example]

## 17.16.5 字段定义

**Field definitions**

=== "中文"

    每个子条款描述了一个独立的字段，每个描述都包含一个标记为语法的部分。该部分包含与该特定字段相关的字段语法部分。这些部分以稍微简化的形式呈现，以帮助理解描述。在这些部分中，左方括号和右方括号表示选项的开始和结束，如 ISO/IEC 14977 中使用的。然而，字段名称、开括号和闭括号表示实际的文字文本，每个逗号也是如此。[注：因此，按照 ISO/IEC 14977 的严格表示，每个字段名称、开括号和闭括号将带有双引号。结束注]
    
    字段集分为以下功能类别：
    
    （类别 | 描述 | 字段）
    
    - **日期和时间**
    
        插入当前日期和/或时间，或某种事件的日期和/或时间。
        
        CREATEDATE ([§17.16.5.11]), DATE ([§17.16.5.13]), EDITTIME ([§17.16.5.16]), PRINTDATE ([§17.16.5.47]), SAVEDATE ([§17.16.5.53]), TIME ([§17.16.5.65])
    
    - **文档自动化**
    
        提供自动化文档处理的功能。
        
        COMPARE ([§17.16.5.10]), DOCVARIABLE ([§17.16.5.15]), GOTOBUTTON ([§17.16.5.23]), IF ([§17.16.5.26]), MACROBUTTON ([§17.16.5.34]), PRINT ([§17.16.5.46])
    
    - **文档信息**
    
        插入或存储有关文档的信息。
        
        AUTHOR ([§17.16.5.4]), COMMENTS ([§17.16.5.9]), DOCPROPERTY ([§17.16.5.14]), FILENAME ([§17.16.5.17]), FILESIZE ([§17.16.5.18]), KEYWORDS ([§17.16.5.30]), LASTSAVEDBY ([§17.16.5.31]), NUMCHARS ([§17.16.5.41]), NUMPAGES ([§17.16.5.42]), NUMWORDS ([§17.16.5.43]), SUBJECT ([§17.16.5.60]), TEMPLATE ([§17.16.5.64]), TITLE ([§17.16.5.66])
    
    - **方程和公式**
    
        定义公式并计算结果；插入符号。
        
        = formula ([§17.16.3]), ADVANCE ([§17.16.5.2]), SYMBOL ([§17.16.5.61])
    
    - **表单字段**
    
        定义支持通过表单控件插入数据的字段。
        
        FORMCHECKBOX ([§17.16.5.20]), FORMDROPDOWN ([§17.16.5.21]), FORMTEXT ([§17.16.5.22])
    
    - **索引和目录**
    
        定义条目，并构建目录、图表目录或法务目录。
        
        INDEX ([§17.16.5.29]), RD ([§17.16.5.50]), TA ([§17.16.5.62]), TC ([§17.16.5.63]), TOA ([§17.16.5.67]), TOC ([§17.16.5.68]), XE ([§17.16.5.72])
    
    - **链接和引用**
    
        插入来自同一文档的其他位置或不同文档或文件的信息。
        
        AUTOTEXT ([§17.16.5.5]), AUTOTEXTLIST ([§17.16.5.6]), BIBLIOGRAPHY ([§17.16.5.7]), CITATION ([§17.16.5.8]) HYPERLINK ([§17.16.5.25]), INCLUDEPICTURE ([§17.16.5.27]), INCLUDETEXT ([§17.16.5.28]), LINK ([§17.16.5.32]), NOTEREF ([§17.16.5.40]), PAGEREF ([§17.16.5.45]), QUOTE ([§17.16.5.49]), REF ([§17.16.5.51]), STYLEREF ([§17.16.5.59])
    
    - **邮件合并**
    
        定义要在邮件合并中使用的信息。邮件合并是将数据集（例如姓名和地址）与 WordprocessingML 文档结合起来，为该数据集中的每条记录生成个性化文档的过程。换句话说，邮件合并是一种操作，通过这种操作，应用程序将某些字段替换为来自相应数据源的每条记录中的数据（有关更多信息，请参见 [§17.14]）。
        
        ADDRESSBLOCK ([§17.16.5.1]), ASK ([§17.16.5.3]), COMPARE ([§17.16.5.10]), DATABASE ([§17.16.5.12]), FILLIN ([§17.16.5.19]), GREETINGLINE ([§17.16.5.24]), IF ([§17.16.5.26]), MERGEFIELD ([§17.16.5.35]), MERGEREC ([§17.16.5.36]), MERGESEQ ([§17.16.5.37]), NEXT ([§17.16.5.38]), NEXTIF ([§17.16.5.39]), SET ([§17.16.5.57]), SKIPIF ([§17.16.5.58])
    
    - **编号**
    
        指定文档项目的编号，例如章节和页面；也包括条形码。
        
        LISTNUM ([§17.16.5.33]), PAGE ([§17.16.5.44]), REVNUM ([§17.16.5.52]), SECTION ([§17.16.5.54]), SECTIONPAGES ([§17.16.5.55]), SEQ ([§17.16.5.56])
    
    - **用户信息**
    
        引用在文档操作中使用的用户账户的姓名、首字母或地址。[注：这些字段可以在文档中使用，允许应用程序在特定用户的上下文中执行实现定义的更新（如果存在这样的上下文）；例如，将当前用户的地址添加到通用表格信函中。结束注]
        
        USERADDRESS ([§17.16.5.69]), USERINITIALS ([§17.16.5.70]), USERNAME ([§17.16.5.71])

=== "英文"
    
    Each of the subclauses below this subclause describes a separate field, and each description contains a section marked Syntax. That section contains pieces of the field grammar as they pertain to that specific field. These pieces are presented in a slightly simpler form to aid in the understanding of the description. In those sections, the left-square-bracket and right-square-bracket designate the start and end of an option, as used in ISO/IEC 14977. However, the field-name, the open-parenthesis and the close-parenthesis designate actual literal text, as does each comma. [Note: Therefore, in a strict presentation according to ISO/IEC 14977, each field-name, open- parenthesis and close-parenthesis would appear with double-quotes surrounding each instance. end note]
    
    The set of fields is divided into the following functional categories:
    
    (Category | Description | Fields)
    
    - **Date and Time**
    
        Inserts the current date and/or time, or date and/or time of some kind of event.
        
        CREATEDATE ([§17.16.5.11]), DATE ([§17.16.5.13]), EDITTIME ([§17.16.5.16]), PRINTDATE ([§17.16.5.47]), SAVEDATE ([§17.16.5.53]), TIME ([§17.16.5.65])
    
    - **Document Automation**
    
        Provides functionality for automated document processing.
        
        COMPARE ([§17.16.5.10]), DOCVARIABLE ([§17.16.5.15]), GOTOBUTTON ([§17.16.5.23]), IF ([§17.16.5.26]), MACROBUTTON ([§17.16.5.34]), PRINT ([§17.16.5.46])
    
    - **Document Information**
    
        Inserts or stores information about the document.
        
        AUTHOR ([§17.16.5.4]), COMMENTS ([§17.16.5.9]), DOCPROPERTY ([§17.16.5.14]), FILENAME ([§17.16.5.17]), FILESIZE ([§17.16.5.18]), KEYWORDS ([§17.16.5.30]), LASTSAVEDBY ([§17.16.5.31]), NUMCHARS ([§17.16.5.41]), NUMPAGES ([§17.16.5.42]), NUMWORDS ([§17.16.5.43]), SUBJECT ([§17.16.5.60]), TEMPLATE ([§17.16.5.64]), TITLE ([§17.16.5.66])
    
    - **Equations and Formulas**
    
        Defines formulas and calculates results; inserts symbols.
        
        = formula ([§17.16.3]), ADVANCE ([§17.16.5.2]), SYMBOL ([§17.16.5.61])
    
    - **Form Fields**
    
        Defines fields that support insertion of data through form controls.
        
        FORMCHECKBOX ([§17.16.5.20]), FORMDROPDOWN ([§17.16.5.21]), FORMTEXT ([§17.16.5.22])
    
    - **Index and Tables**
    
        Defines entries for, and builds, a table of contents, table of figures, or table of authorities.
        
        INDEX ([§17.16.5.29]), RD ([§17.16.5.50]), TA ([§17.16.5.62]), TC ([§17.16.5.63]), TOA ([§17.16.5.67]), TOC ([§17.16.5.68]), XE ([§17.16.5.72])
    
    - **Links and References**
    
        Inserts information from another place in the same document or from a different document or file.
        
        AUTOTEXT ([§17.16.5.5]), AUTOTEXTLIST ([§17.16.5.6]), BIBLIOGRAPHY ([§17.16.5.7]), CITATION ([§17.16.5.8]) HYPERLINK ([§17.16.5.25]), INCLUDEPICTURE ([§17.16.5.27]), INCLUDETEXT ([§17.16.5.28]), LINK ([§17.16.5.32]), NOTEREF ([§17.16.5.40]), PAGEREF ([§17.16.5.45]), QUOTE ([§17.16.5.49]), REF ([§17.16.5.51]), STYLEREF ([§17.16.5.59])
    
    - **Mail Merge**
    
        Defines information that is to be used in a mail merge. A mail merge is a process by which a data set (e.g., of names and addresses) is combined with a WordprocessingML document to produce a customized document for each record in said data set. In other words, a mail merge is an operation by which an application replaces certain fields with the data in each record from a corresponding data source (see [§17.14] for additional information).
        
        ADDRESSBLOCK ([§17.16.5.1]), ASK ([§17.16.5.3]), COMPARE ([§17.16.5.10]), DATABASE ([§17.16.5.12]), FILLIN ([§17.16.5.19]), GREETINGLINE ([§17.16.5.24]), IF ([§17.16.5.26]), MERGEFIELD ([§17.16.5.35]), MERGEREC ([§17.16.5.36]), MERGESEQ ([§17.16.5.37]), NEXT ([§17.16.5.38]), NEXTIF ([§17.16.5.39]), SET ([§17.16.5.57]), SKIPIF ([§17.16.5.58])
    
    - **Numbering**
    
        Specifies numbering for document items such as sections and pages; also bar codes.
        
        LISTNUM ([§17.16.5.33]), PAGE ([§17.16.5.44]), REVNUM ([§17.16.5.52]), SECTION ([§17.16.5.54]), SECTIONPAGES ([§17.16.5.55]), SEQ ([§17.16.5.56])
    
    - **User Information**
    
        Referencesthe name, initials, or address of a user account under which the document is manipulated. [Note: These fields can be used in documents to allow applications to perform implementation-defined updates under a particular user’s context (if such a context exists); for example, to add the address of the current user to a generic form letter. end note]
        
        USERADDRESS ([§17.16.5.69]), USERINITIALS ([§17.16.5.70]), USERNAME ([§17.16.5.71])

### 17.16.5.1 地址块(ADDRESSBLOCK)

**ADDRESSBLOCK**

=== "中文"

=== "英文"

### 17.16.5.2 前进(ADVANCE)

**ADVANCE**

=== "中文"

    **语法**: ADVANCE [ switches ]
    
    **描述**: 当文档中的文本被渲染时，通常情况下，每个字符都会紧跟在前一个内容（另一个字符、图像等）之后显示，根据底层WordprocessingML的词法顺序。此字段的存在将文本的起始显示点向右、向左、向上、向下或特定的水平或垂直位置移动。它不影响其他运行内容（例如图像）的显示。此字段使用的开关在显示时可能导致文本重叠。如果文本在固定页面的限制范围内显示，重新定位的文本将不会显示，如果它移动到当前页面的打印边距之外（即使目标位置在前/后页面上逻辑上出现）。
    
    **字段值**: 无。
    
    **开关**: 以下是零个或多个特定于字段的开关。
    
    <table border=1>
        <tr>
            <td>d *field-argument*</td>
            <td>将跟随该字段的文本向下移动由该开关的字段参数中指定的整数点数。</td>
        </tr>
        <tr>
            <td>l *field-argument*</td>
            <td>将跟随该字段的文本向左移动由该开关的字段参数中指定的整数点数。</td>
        </tr>
        <tr>
            <td>r *field-argument*</td>
            <td>将跟随该字段的文本向右移动由该开关的字段参数中指定的整数点数。</td>
        </tr>
        <tr>
            <td>u *field-argument*</td>
            <td>将跟随该字段的文本向上移动由该开关的字段参数中指定的整数点数。</td>
        </tr>
        <tr>
            <td>x *field-argument*</td>
            <td>将跟随该字段的文本从列、框架或文本框的左边缘向右移动由该开关的字段参数中指定的整数点数。</td>
        </tr>
        <tr>
            <td>y *field-argument*</td>
            <td>将跟随该字段的文本向上移动由该开关的字段参数中指定的整数点数。此移动是相对于页面的垂直位置。整个包含该字段的文本行将被移动。如果此开关指定的位置在页面边距之外，或者如果在以下任何位置使用该开关：表格、文本框、脚注、尾注、注释、页眉或页脚，则此开关将被忽略。</td>
        </tr>
    </table>
    
    [示例: 当显示以下WordprocessingML时:
    
    ```xml
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE u 6"/>
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE d 12"/>
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE l 20"/>
    <w:r>
        <w:t>+</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE x 150"/>
    <w:r>
        <w:t>ZZ</w:t>
    </w:r>
    ```
    
    结果为:
    
    <figure markdown="span">
      ![Image title](./imgs/16img01.png)
    </figure>
    
    示例结束]

=== "英文"
    
    **Syntax**: ADVANCE [ switches ]
    
    **Description**: When text within a document is rendered, typically, each character is displayed immediately following the previous piece of content (another character, an image, and so on), according to the lexical order of the underlying WordprocessingML. The presence of this field moves the starting point at which the text that lexically follows the field is displayed to the right or left, up or down, or to a specific horizontal or vertical position. It does not affect the display of other run content (e.g., images). The switches used by this field can cause text to overlap when it is displayed. If the text is displayed within the constraints of a fixed page, repositioned text is not display if it is moved beyond the print margins of the current page (even if the target location would logically appear on a previous/following page).
    
    **Field Value**: None.
    
    **Switches**: Zero or more of the following field-specific-switches.
    
    <table border=1>
        <tr>
            <td>\d field-argument</td>
            <td>Moves the text that follows the field down by the integral number of points specified by text in this switch's field-argument.</td>
        </tr>
        <tr>
            <td>\l field-argument</td>
            <td>Moves the text that follows the field left by the integral number of points specified by text in this switch's field-argument.</td>
        </tr>
        <tr>
            <td>\r field-argument</td>
            <td>Moves the text that follows the field right by the integral number of points specified by text in this switch's field-argument.</td>
        </tr>
        <tr>
            <td>\u field-argument</td>
            <td>Moves the text that follows the field up by the integral number of points specified by text in this switch's field-argument.</td>
        </tr>
        <tr>
            <td>\x field-argument</td>
            <td>Moves the text that follows the field the integral number of points specified by text in this switch's field-argument from the left edge of the column, frame, or text box.</td>
        </tr>
        <tr>
            <td>\y field-argument</td>
            <td>Moves the text that follows the field the integral number of points specified by text in this switch's field-argument. This shift is the vertical position relative to the page. The entire line of text that contains the field is moved. This switch is ignored if it specifies a location outside the page margins or if the switch is used inside any of the following: table, text box, footnote, endnote, annotation, header, or footer.</td>
        </tr>
    </table>
    
    [Example: When the following WordprocessingML is displayed:
    
    ```xml
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE \u 6"/>
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE \d 12"/>
    <w:r>
        <w:t>XX</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE \l 20"/>
    <w:r>
        <w:t>+</w:t>
    </w:r>
    <w:fldSimple w:instrText="ADVANCE \x 150"/>
    <w:r>
        <w:t>ZZ</w:t>
    </w:r>
    ```
    
    The results are:
    
    [111](./imgs/16img01.png)
    
    end example]

### 17.16.5.3 询问(ASK)

**ASK**

=== "中文"

=== "英文"

### 17.16.5.4 作者(AUTHOR)

**AUTHOR**

=== "中文"

=== "英文"

### 17.16.5.5 自动文本(AUTOTEXT)

**AUTOTEXT**

=== "中文"

=== "英文"

### 17.16.5.6 自动文本列表(AUTOTEXTLIST)

**AUTOTEXTLIST**

=== "中文"

=== "英文"

### 17.16.5.7 参考目录(BIBLIOGRAPHY)

**BIBLIOGRAPHY**

=== "中文"

=== "英文"

### 17.16.5.8 引文(CITATION)

**CITATION**

=== "中文"

=== "英文"

### 17.16.5.9 注释(COMMENTS)

**COMMENTS**

=== "中文"

=== "英文"

### 17.16.5.10 比较(COMPARE)

**COMPARE**

=== "中文"

=== "英文"

### 17.16.5.11 创建日期(CREATEDATE)

**CREATEDATE**

=== "中文"

=== "英文"

### 17.16.5.12 数据库(DATABASE)

**DATABASE**

=== "中文"

=== "英文"

### 17.16.5.13 日期(DATE)

**DATE**

=== "中文"

=== "英文"

### 17.16.5.14 文档属性(DOCPROPERTY)

**DOCPROPERTY**

=== "中文"

=== "英文"

### 17.16.5.15 文档变量(DOCVARIABLE)

**DOCVARIABLE**

=== "中文"

=== "英文"

### 17.16.5.16 编辑时间(EDITTIME)

**EDITTIME**

=== "中文"

=== "英文"

### 17.16.5.17 文件名(FILENAME)

**FILENAME**

=== "中文"

=== "英文"

### 17.16.5.18 文件大小(FILESIZE)

**FILESIZE**

=== "中文"

=== "英文"

### 17.16.5.19 填写(FILLIN)

**FILLIN**

=== "中文"

=== "英文"

### 17.16.5.20 表单复选框(FORMCHECKBOX)

**FORMCHECKBOX**

=== "中文"

=== "英文"

### 17.16.5.21 表单下拉菜单(FORMDROPDOWN)

**FORMDROPDOWN**

=== "中文"

=== "英文"

### 17.16.5.22 表格文本(FORMTEXT)

**FORMTEXT**

=== "中文"

=== "英文"

### 17.16.5.23 转到按钮(GOTOBUTTON)

**GOTOBUTTON**

=== "中文"

=== "英文"

### 17.16.5.24 问候语(GREETINGLINE)

**GREETINGLINE**

=== "中文"

=== "英文"

### 17.16.5.25 超链接(HYPERLINK)

**HYPERLINK**

=== "中文"

=== "英文"

### 17.16.5.26 如果(IF)

**IF**

=== "中文"

=== "英文"

### 17.16.5.27 包含图片(INCLUDEPICTURE)

**INCLUDEPICTURE**

=== "中文"

=== "英文"

### 17.16.5.28 包含文本(INCLUDETEXT)

**INCLUDETEXT**

=== "中文"

=== "英文"

### 17.16.5.29 索引(INDEX)

**INDEX**

=== "中文"

=== "英文"

### 17.16.5.30 关键词(KEYWORDS)

**KEYWORDS**

=== "中文"

=== "英文"

### 17.16.5.31 最后保存者(LASTSAVEDBY)

**LASTSAVEDBY**

=== "中文"

=== "英文"

### 17.16.5.32 链接(LINK)

**LINK**

=== "中文"

=== "英文"

### 17.16.5.33 列表编号(LISTNUM)

**LISTNUM**

=== "中文"

=== "英文"

### 17.16.5.34 宏按钮(MACROBUTTON)

**MACROBUTTON**

=== "中文"

=== "英文"

### 17.16.5.35 合并字段(MERGEFIELD)

**MERGEFIELD**

=== "中文"

=== "英文"

### 17.16.5.36 合并记录(MERGEREC)

**MERGEREC**

=== "中文"

=== "英文"

### 17.16.5.37 合并序列(MERGESEQ)

**MERGESEQ**

=== "中文"

=== "英文"

### 17.16.5.38 下一个(NEXT)

**NEXT**

=== "中文"

=== "英文"

### 17.16.5.39 下一个如果(NEXTIF)

**NEXTIF**

=== "中文"

=== "英文"

### 17.16.5.40 注意参考(NOTEREF)

**NOTEREF**

=== "中文"

=== "英文"

### 17.16.5.41 字符数(NUMCHARS)

**NUMCHARS**

=== "中文"

=== "英文"

### 17.16.5.42 页数(NUMPAGES)

**NUMPAGES**

=== "中文"

=== "英文"

### 17.16.5.43 词数(NUMWORDS)

**NUMWORDS**

=== "中文"

=== "英文"

### 17.16.5.44 页(PAGE)

**PAGE**

=== "中文"

=== "英文"

### 17.16.5.45 页面参考(PAGEREF)

**PAGEREF**

=== "中文"

=== "英文"

### 17.16.5.46 打印(PRINT)

**PRINT**

=== "中文"

=== "英文"

### 17.16.5.47 打印日期(PRINTDATE)

**PRINTDATE**

=== "中文"

=== "英文"

### 17.16.5.48 私有(PRIVATE)

**PRIVATE**

=== "中文"

=== "英文"

### 17.16.5.49 引用(QUOTE)

**QUOTE**

=== "中文"

=== "英文"

### 17.16.5.50 rd(RD)

**RD**

=== "中文"

=== "英文"

### 17.16.5.51 引用(REF)

**REF**

=== "中文"

=== "英文"

### 17.16.5.52 版本号(REVNUM)

**REVNUM**

=== "中文"

=== "英文"

### 17.16.5.53 保存日期(SAVEDATE)

**SAVEDATE**

=== "中文"

=== "英文"

### 17.16.5.54 节(SECTION)

**SECTION**

=== "中文"

=== "英文"

### 17.16.5.55 节页面(SECTIONPAGES)

**SECTIONPAGES**

=== "中文"

=== "英文"

### 17.16.5.56 序列(SEQ)

**SEQ**

=== "中文"

=== "英文"

### 17.16.5.57 集合(SET)

**SET**

=== "中文"

=== "英文"

### 17.16.5.58 跳过如果(SKIPIF)

**SKIPIF**

=== "中文"

=== "英文"

### 17.16.5.59 样式引用(STYLEREF)

**STYLEREF**

=== "中文"

=== "英文"

### 17.16.5.60 主题(SUBJECT)

**SUBJECT**

=== "中文"

=== "英文"

### 17.16.5.61 符号(SYMBOL)

**SYMBOL**

=== "中文"

=== "英文"

### 17.16.5.62 ta(TA)

**TA**

=== "中文"

=== "英文"

### 17.16.5.63 tc(TC)

**TC**

=== "中文"

=== "英文"

### 17.16.5.64 模板(TEMPLATE)

**TEMPLATE**

=== "中文"

=== "英文"

### 17.16.5.65 时间(TIME)

**TIME**

=== "中文"

=== "英文"

### 17.16.5.66 (TITLE)

**TITLE**

=== "中文"

=== "英文"

### 17.16.5.67 标题(TOA)

**TOA**

=== "中文"

=== "英文"

### 17.16.5.68 目录(TOC)

**TOC**

=== "中文"

=== "英文"

### 17.16.5.69 用户地址(USERADDRESS)

**USERADDRESS**

=== "中文"

=== "英文"

### 17.16.5.70 用户姓名缩写(USERINITIALS)

**USERINITIALS**

=== "中文"

=== "英文"

### 17.16.5.71 用户名(USERNAME)

**USERNAME**

=== "中文"

=== "英文"

### 17.16.5.72 xe(XE)

**XE**

=== "中文"

=== "英文"


## 17.16.6 calcOnExit (当前字段修改时重新计算字段)

**calcOnExit (Recalculate Fields When Current Field Is Modified)**

=== "中文"
    
    该元素指定在修改父表单字段的内容时，当前WordprocessingML文档中所有字段的当前内容都将从其字段代码重新计算。【注：应用程序有权决定单次修改的范围，例如，当用户在用户界面中移动插入点时，或在每次按键后等。结束注】
    
    如果省略了此元素，则修改当前字段的内容不会导致重新计算当前文档中的所有字段。
    
    【示例：考虑以下WordprocessingML片段，其中包含文档中两个字段的内容：
    
    ```xml
    <w:bookmarkStart w:name="Text1" … />
        <w:r>
            <w:fldChar w:fldCharType="begin">
                <w:ffData>
                    <w:calcOnExit/>
                    …
                </w:ffData>
            </w:fldChar>
            </w:r>
            <w:r>
                <w:instrText> FORMTEXT </w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            <w:r>
                <w:t>1</w:t>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="end"/>
            </w:r>
            <w:bookmarkEnd … />
            <w:fldSimple w:instr="=Text1+10">
                <w:r>
                    <w:t>11</w:t>
                </w:r>
            </w:fldSimple>
    ```
    
    上述第一个字段（文本表单字段）的当前值为1，但还有calcOnExit元素存在（因此继承了其默认属性值为true）。这意味着如果将此表单字段的值更改为10，则必须自动更新文档中的所有字段，导致第二个字段的值自动更改为20。结束示例】
    
    该元素的内容模型由[§17.17.4]中的常见布尔属性定义定义。

=== "英文"
    
    This element specifies that the current contents of all fields within the current WordprocessingML document shall be recalculated from their field codes when the contents of the parent form field are modified. [Note: It is at the discretion of an application to determine the scope of a single modification, for example, when the user moves the insertion point in a user interface, or after each keystroke, etc. end note]
    
    If this element is omitted, then modification of the contents of the current field shall not result in all fields in the current document being recalculated.
    
    [Example: Consider the following WordprocessingML fragment for the contents of two fields in a document:
    
    ```xml
    <w:bookmarkStart w:name="Text1" … />
        <w:r>
            <w:fldChar w:fldCharType="begin">
                <w:ffData>
                    <w:calcOnExit/>
                    …
                </w:ffData>
            </w:fldChar>
            </w:r>
            <w:r>
                <w:instrText> FORMTEXT </w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            <w:r>
                <w:t>1</w:t>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="end"/>
            </w:r>
            <w:bookmarkEnd … />
            <w:fldSimple w:instr="=Text1+10">
                <w:r>
                    <w:t>11</w:t>
                </w:r>
            </w:fldSimple>
    ```
    
    The first field above (the text form field) has a current value of 1, but also has the calcOnExit element present (therefore inheriting its default attribute value of true). This means that if the value of this form field is changed to 10, that all fields in the document must automatically be updated, resulting in the second field's value being automatically changed to 20. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].



## 17.16.7 checkBox (复选框表单字段属性)

**checkBox (Checkbox Form Field Properties)**

=== "中文"
    
    该元素指定一组属性，这些属性将与文档中的父FORMCHECKBOX复选框表单字段（[§17.16.5.20]）关联。
    
    如果父表单字段不是复选框（即，其字段代码的值不是FORMCHECKBOX），则可以忽略这些属性。
    
    【示例：考虑以下复选框表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:checkBox>
            <w:size w:val="20" />
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    checkBox元素指定它包含父复选框表单字段的一组属性。在此示例中，这些属性指定复选框的大小必须通过size元素（[§17.16.29]）确切地为10点，并且复选框的当前状态必须通过checked元素（[§17.16.8]）进行检查。

    结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFCheckBox) is located in §A.1. end note]

=== "英文"
    
    This element specifies a set of properties which shall be associated with the parent FORMCHECKBOX checkbox form field ([§17.16.5.20]) within the document.
    
    If the parent form field is not a checkbox (i.e. its field code does not have a value of FORMCHECKBOX), then these properties can be ignored.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a checkbox form field:
    
    ```xml
    <w:ffData>
        <w:checkBox>
            <w:size w:val="20" />
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    The checkBox element specifies that it contains a set of properties for the parent checkbox form field. In this case, these properties specify that the size of the checkbox must be exactly 10 points via the size element ([§17.16.29]), and that the current state of the checkbox must be checked via the checked element ([§17.16.8]).
    end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFCheckBox) is located in §A.1. end note]

## 17.16.8 checked (复选框表单字段状态)

**checked (Checkbox Form Field State)**

=== "中文"
    
    该元素指定复选框表单字段的当前状态。该值将用于指定复选框的当前值，该值是显式选择的值，而不是默认值，该默认值使用default元素（[§17.16.12]）指定。
    
    如果省略此元素，则父表单字段复选框没有状态，并且其状态将基于复选框表单字段属性中default元素的值确定。
    
    【示例：考虑以下复选框表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:checkBox>
            …
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    checked元素指定复选框的当前状态为选中（通过属性值true）。结束示例】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies the current state for a checkbox form field. This value shall be used to specify the current value for a checkbox as explicitly chosen for that checkbox, as opposed its default value, which is specified using the default element ([§17.16.12]).
    
    If this element is omitted, then the parent form field checkbox has no state, and its state shall be determined based on the value of the default element in the checkbox form field properties.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a checkbox form field:
    
    ```xml
    <w:ffData>
        <w:checkBox>
            …
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    The checked element specifies that the current state of the checkbox is checked (via an attribute value of true). end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

## 17.16.9 ddList (下拉列表表单字段属性)

**ddList (Drop-Down List Form Field Properties)**

=== "中文"
    
    该元素指定一组属性，这些属性将与文档中的父FORMDROPDOWN下拉列表表单字段（[§17.16.5.21]）相关联。
    
    如果父表单字段不是下拉列表（即其字段代码没有值为FORMDROPDOWN），则可以忽略这些属性。
    
    【示例：考虑以下用于下拉列表表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:ddList>
            <w:listEntry w:val="One" />
            <w:listEntry w:val="Two" />
            <w:listEntry w:val="Three" />
        </w:ddList>
    </w:ffData>
    ```
    
    ddList元素指定它包含一组父下拉列表表单字段的属性。在这种情况下，这些属性指定下拉列表必须包含三个条目One、Two和Three，通过listEntry元素（[§17.16.25]）。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFDDList) is located in §A.1. end note]

=== "英文"
    
    This element specifies a set of properties which shall be associated with the parent FORMDROPDOWN drop-down list form field ([§17.16.5.21]) within the document.
    
    If the parent form field is not a drop-down list (i.e. its field code does not have a value of FORMDROPDOWN), then these properties can be ignored.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a drop-down list form field:
    
    ```xml
    <w:ffData>
        <w:ddList>
            <w:listEntry w:val="One" />
            <w:listEntry w:val="Two" />
            <w:listEntry w:val="Three" />
        </w:ddList>
    </w:ffData>
    ```
    
    The ddList element specifies that it contains a set of properties for the parent drop-down list form field. In this case, these properties specify that the drop-down list must contain three entries of One, Two, and Three via the listEntry elements ([§17.16.25]). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFDDList) is located in §A.1. end note]

## 17.16.10 default (默认文本框表单字段字符串)

**default (Default Text Box Form Field String)**

=== "中文"
        
    该元素指定父文本框表单字段的默认字符串。如果其当前运行内容为空（即文本框内没有实际内容），则该字符串是将显示在文档故事中的内容。如果当前表单字段的类型（[§17.16.34]）为计算，则此字符串应包含要执行的计算。
    
    如果省略此元素，则当前文本框表单字段将不具有默认值。
    
    【示例：考虑以下文本框表单字段的WordprocessingML片段：
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:textInput>
                <w:default w:val="No content."/>
            </w:textInput>
        </w:ffData>
    </w:fldChar>
    ```
    
    default元素指定文本框表单字段的默认值为“No content.”。由于表单字段不包含任何值，因此在应用程序显示表单字段的内容时，将显示此内容。结束示例】
    
    ??? abstract "属性"
    
        - **val**（字符串值）
        
            指定其内容包含一个字符串。
    
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
                    
            在这种情况下,val属性中的十进制数字是最接近的上级结构化文档标签的标题。在每种情况下,该值都是在父元素的上下文中解释的。[end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the default string for the parent text box form field. This string is the content which shall be displayed in the document story within this form field if its current run contents are empty (i.e. there is not actual content within the text box). If the type ([§17.16.34]) of the current form field is calculation, then this string shall hold the calculation to be performed.
    
    If this element is omitted, then the current text box form field shall not have a default value.
    
    [Example: Consider the following WordprocessingML fragment for a text box form field:
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:textInput>
                <w:default w:val="No content."/>
            </w:textInput>
        </w:ffData>
    </w:fldChar>
    ```
    
    The default element specifies the default value of the text box form field to be No content.Since the form field does not contain any value, this is the content which must be displayed when the contents of the form field are displayed by an application. end example]

    ??? abstract "Attributes"

        - **val** (String Value)
        
            Specifies that its contents contain a string.

            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
            
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

## 17.16.11 default (默认下拉列表项目索引)

**default (Default Drop-Down List Item Index)**

=== "中文"
    
    这个元素指定了父下拉列表表单字段的默认条目的从零开始的索引。如果没有选择任何元素（即结果元素（[§17.16.28]）被省略），则此索引值是在文档中的故事中此表单字段内显示的下拉列表中的值。
    
    如果省略了此元素，则当前的下拉列表表单字段将具有默认值0（它的第一个条目）。如果属性值引用不存在的索引值（即负数或超出下拉列表中项目数量的数字），则可以忽略此值，并且当前的下拉列表表单字段将具有默认值0（它的第一个条目）。
    
    【示例：考虑下面的下拉列表表单字段的WordprocessingML片段：
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:ddList>
                <w:default w:val="1" />
                <w:listEntry w:val="One" />
                <w:listEntry w:val="Two" />
                <w:listEntry w:val="Three" />
            </w:ddList>
        </w:ffData>
    </w:fldChar>
    ```
    
    默认元素指定了下拉列表表单字段的默认值的索引为1。由于表单字段不包含结果元素，这是在应用程序显示表单字段的内容时必须显示的内容的索引。在这种情况下，生成的默认值文本是“Two”。结束示例】
    
    ??? abstract "属性"
    
        - **val**（十进制数值）
        
            指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑下面简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须在父元素的上下文中解释。结束示例】
            
            此属性的可能值由 ST_DecimalNumber 简单类型（[§17.18.10]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the zero-based index of the default entry for the parent drop-down list form field. This index value is the value within the drop-down list which shall be displayed in the document story within this form field if no element is selected (i.e. the result element ([§17.16.28]) is omitted).
    
    If this element is omitted, then the current drop-down list form field shall have a default value of 0 (its first entry). If the attribute value references an index value which does not exist (i.e. a negative number or a number that exceeds the number of items in the drop-down list), then this value can be ignored and the current drop-down list form field shall have a default value of 0 (its first entry).
    
    [Example: Consider the following WordprocessingML fragment for a drop-down list form field:
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:ddList>
                <w:default w:val="1" />
                <w:listEntry w:val="One" />
                <w:listEntry w:val="Two" />
                <w:listEntry w:val="Three" />
            </w:ddList>
        </w:ffData>
    </w:fldChar>
    ```
    
    The default element specifies the index of the default value of the drop-down list form field to be 1.Since the form field does not contain a result element, this is the index of the content which must be displayed when the contents of the form field are displayed by an application. In this case, the resulting default value text is Two. end example]
    
    ??? abstract "Attributes"
    
        - **val** (Decimal Number Value)
        
            Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.16.12 default (默认复选框表单字段状态)

**default (Default Checkbox Form Field State)**

=== "中文"
    
    该元素指定了父复选框表单字段的默认复选框状态。该值确定了当其当前运行内容为空时的复选框状态（即下拉列表中没有实际内容）。
    
    如果省略了此元素，则当前复选框表单字段将具有默认值0（未选中）。
    
    【示例：考虑下面的复选框列表表单字段的WordprocessingML片段：
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:checkBox>
                <w:default w:val="true" />
            </w:checkBox>
        </w:ffData>
    </w:fldChar>
    ```
    
    默认元素指定了复选框表单字段的默认状态为true。由于表单字段不包含任何运行内容，这是应用程序显示表单字段内容时必须显示的状态。结束示例】
    
    该元素的内容模型由[§17.17.4]中的常见布尔属性定义。

=== "英文"
    
    This element specifies the default checkbox state for the parent checkbox form field. This value determines the checkbox state when its current run contents are empty (i.e. there is not actual content within the drop-down list).
    
    If this element is omitted, then the current checkbox form field shall have a default value of 0 (unchecked).
    
    [Example: Consider the following WordprocessingML fragment for a checkbox list form field:
    
    ```xml
    <w:fldChar w:fldCharType="begin">
        <w:ffData>
            <w:checkBox>
                <w:default w:val="true" />
            </w:checkBox>
        </w:ffData>
    </w:fldChar>
    ```
    
    The default element specifies the default state of the checkbox form field to be true.Since the form field does not contain any run content, this is the state which must be displayed when the contents of the form field are displayed by an application. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

## 17.16.13 delInstrText (删除的字段代码)

**delInstrText (Deleted Field Code)**

=== "中文"
    
    该元素指定了此运行包含文档中复杂字段内的已删除字段代码（[§17.16.5]）。delInstrText 元素应用于所有包含字段代码的运行，这些代码是包含在使用 del 元素（[§17.13.5.14]）删除的文本区域的一部分。
    
    如果此元素未包含在 del 元素内，则文档不符合规范。如果此元素包含在不是复杂字段字段代码一部分的运行内，则应将其处理为常规已删除文本。
    
    【示例：考虑WordprocessingML文档中的复杂字段，该字段已从文本框表单字段更改为启用了修订跟踪的复选框表单字段。因此，该字段将表示为：
    
    ```xml
    <w:fldChar w:fldCharType="begin" />
    <w:ins>
        <w:r>
            <w:instrText>FORMCHECKBOX</w:instrText>
        </w:r>
    </w:ins>
    <w:del>
        <w:r>
            <w:delInstrText>FORMFIELDTEXT</w:delInstrText>
        </w:r>
    </w:del>
    <w:fldChar w:fldCharType="separate" />
    …
    <w:fldChar w:fldCharType="end" />
    ```
    
    已删除的字段代码包含在 delInstrText 节点中，而插入（和当前的）字段代码包含在 instrText 节点中。结束示例】
    
    ??? abstract "属性"
    
        - **xml:space**（内容包含显著空白）
        
            命名空间：http://www.w3.org/XML/1998/namespace
            
            使用 W3C 空间保留规则指定如何处理此元素内容的空格。
            
            【示例：考虑包含在 WordprocessingML 文档中的以下运行：
            
            ```xml
                <w:r>
                    <w:t> significant whitespace     </w:t>
                </w:r>
            ```
            
            尽管在运行中的文本内容两侧都有三个空格，但该空白并未明确标记为显著，因此它受当前在该运行范围内指定的空间保留规则的约束。结束示例】
            
            此属性的可能值由 XML 1.0 规范的§2.10定义。
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_Text) is located in §A.1. end note]

=== "英文"
    
    This element specifies that this run contains deleted field codes ([§17.16.5]) within a complex field in the document. The delInstrText element shall be used for all runs containing field codes which are part of a region of text that is contained in a deleted region using the del element ([§17.13.5.14]).
    
    If this element is not contained within a del element, then the document is non-conformant. If this element is contained within a run which is not part of a complex field's field codes, then it should be handled as regular deleted text.
    
    [Example: Consider a complex field within a WordprocessingML document which was changed from a text box form field to a checkbox form field with revision tracking enabled. This field would therefore be represented as follows:
    
    ```xml
    <w:fldChar w:fldCharType="begin" />
    <w:ins>
        <w:r>
            <w:instrText>FORMCHECKBOX</w:instrText>
        </w:r>
    </w:ins>
    <w:del>
        <w:r>
            <w:delInstrText>FORMFIELDTEXT</w:delInstrText>
        </w:r>
    </w:del>
    <w:fldChar w:fldCharType="separate" />
    …
    <w:fldChar w:fldCharType="end" />
    ```
    
    The deleted field code is contained in a delInstrText node, while the inserted (and current) field code is contained in an instrText node. end example]
    
    ??? abstract "Attributes"
    
        - **xml:space** (Content Contains Significant Whitespace)
    
            Namespace: http://www.w3.org/XML/1998/namespace
    
            Specifies how white space should be handled for the contents of this element using the W3C space preservation rules.
    
            [Example: Consider the following run contained within a WordprocessingML document:
            
            ```xml
                <w:r>
                    <w:t> significant whitespace     </w:t>
                </w:r>
            ```
            
            Although there are three spaces on each side of the text content in the run, that whitespace has not been specifically marked as significant, therefore it is subject to the space preservation rules currently specified in that run's scope. end example]
            
            The possible values for this attribute are defined by §2.10 of the XML 1.0 specification.
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_Text) is located in §A.1. end note]


## 17.16.14 enabled (启用表单字段)

**enabled (Form Field Enabled)**

=== "中文"
        
    该元素指定了当文档中显示父表单字段时，其是否应表现为启用或禁用状态。除非文档的设置部分指定当前文档的 documentProtection 元素处于允许填写表单字段的状态，否则此设置对该表单字段的行为没有影响。
    
    如果省略了此元素，则当文档设置指定文档允许填写表单字段时，父表单字段将处于启用状态。
    
    【示例：考虑以下文本框表单字段的WordprocessingML片段：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin" >
            <w:ffData>
                <w:enabled w:val="false"/>
                <w:textInput>
                    …
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    enabled 元素指定当前文本框表单字段的状态为禁用；因此，即使 documentProtection 元素的状态明确允许编辑表单字段，该文本框在当前文档中也不可编辑。结束示例】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies whether the parent form field shall behave as though it is enabled or disabled when it is displayed in the document. This setting shall have no effect on the behavior of this form field unless the document's Settings part specifies that the documentProtection element for the current document is in a state allowing the filling in of form fields.
    
    If this element is omitted, then the parent form field shall be in its enabled state when the document settings specify that the document allows the filling-in of form fields.
    
    ```xml
    [Example: Consider the following WordprocessingML fragment for a text box form field:
    <w:r>
        <w:fldChar w:fldCharType="begin" >
            <w:ffData>
                <w:enabled w:val="false"/>
                <w:textInput>
                    …
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The enabled element specifies that the state of the current text box form field is disabled; therefore this text box must not be editable within the current document even when the state of the documentProtection element specifically allows the editing of form fields. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

## 17.16.15 entryMacro (在表单字段输入上执行的脚本函数)

**entryMacro (Script Function to Execute on Form Field Entry)**

=== "中文"
    
    该元素指定了在输入父表单字段的运行内容时应执行的脚本语言中的子例程。该子例程的语言和位置可以由应用程序使用所需的任何方法确定。【注：应用程序有权确定“输入”表单字段的范围和时机，例如，当用户在用户界面中移动插入点时，或者在没有用户界面的应用程序执行每个操作时等。结束注】
    
    如果省略了此元素，则不应与输入父表单字段的运行内容关联任何子例程。如果此元素指定了无法定位或不受应用程序支持的宏，则其值可以被忽略，但在重新保存文件时不应丢失。
    
    【示例：考虑以下复选框表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:entryMacro w:val="TestEntryFunction" />
        <w:checkBox>
            …
        </w:checkBox>
    </w:ffData>
    ```
    
    entryMacro 元素指定了处理此文件的任何应用程序应尝试定位并执行名为 TestEntryFunction 的脚本子例程，当复选框的内容被输入时。如果无法定位或执行此子例程，则会静默地忽略此设置。结束示例】
    
    ??? abstract "属性"
    
        - **val**（脚本函数名称）
        
            指定一个与父元素关联的单个脚本子例程的名称。其使用取决于父 XML 元素的上下文。
            
            【示例：考虑以下表单字段属性的WordprocessingML片段：
            
            ```xml
            <w:ffData>
                <w:exitMacro w:val="HelloWorld" />
            </w:ffData>
            ```
            
            val 属性指定了在父元素上下文中必须使用名为 HelloWorld 的脚本函数；在这种情况下，在退出字段时执行。结束示例】
            
            此属性的可能值由 ST_MacroName 简单类型（[§17.18.51]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MacroName) is located in §A.1. end note]

=== "英文"
    
    This element specifies a subroutine in a scripting language which should be executed when the when the run contents of the parent form field are entered. The language and location of this subroutine can be determined using any method desired by an application. [Note: It is at the discretion of an application to determine the scope and timing of "entering" a form field, for example, when the user moves the insertion point in a user interface or upon each operation by an application without a user interface, etc. end note]
    
    If this element is omitted, then no subroutine shall be associated with entering the run contents of the parent form field. If this element specifies a macro which cannot be located or is not supported by an application, then its value can be ignored, but shall not be lost upon resaving the file.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a checkbox form field:
    
    ```xml
    <w:ffData>
        <w:entryMacro w:val="TestEntryFunction" />
        <w:checkBox>
            …
        </w:checkBox>
    </w:ffData>
    ```
    
    The entryMacro element specifies that any application which processes this file should attempt to locate and execute a scripting subroutine called TestEntryFunction when the contents of the checkbox are entered. If this subroutine cannot be located or executed, then this setting is silently ignored. end example]
    
    ??? abstract "Attributes"
    
        - **val** (Name of Script Function)
    
            Specifies the name of a single scripting subroutine which shall be associated with the parent element. Its use is specifies based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment for the properties of a form field:
            
            ```xml
            <w:ffData>
                <w:exitMacro w:val="HelloWorld" />
            </w:ffData>
            ```
            
            The val attribute specifies that a script function called HelloWorld must be used in the context of the parent element; in this case, to execute when the field is exited. end example]
            
            The possible values for this attribute are defined by the ST_MacroName simple type ([§17.18.51]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MacroName) is located in §A.1. end note]

## 17.16.16 exitMacro (在表单字段退出时执行的脚本函数)

**exitMacro (Script Function to Execute on Form Field Exit)**

=== "中文"
    
    该元素指定了在退出父表单字段的运行内容时应执行的脚本语言中的子例程。该子例程的语言和位置可以由应用程序使用所需的任何方法确定。【注：应用程序有权确定“退出”表单字段的范围和时机，例如，当用户在用户界面中移动插入点时，或者在没有用户界面的应用程序执行每个操作时等。结束注】
    
    如果省略了此元素，则不应与退出父表单字段的运行内容关联任何子例程。如果此元素指定了无法定位或不受应用程序支持的宏，则其值可以被忽略，但在重新保存文件时不应丢失。
    
    【示例：考虑以下表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:exitMacro w:val="TestExitFunction" />
    </w:ffData>
    ```
    
    exitMacro 元素指定了处理此文件的任何应用程序应尝试定位并执行名为 TestExitFunction 的脚本子例程，当表单字段的内容被退出时。如果无法定位或执行此子例程，则会静默地忽略此设置。结束示例】
    
    ??? abstract "属性"
        
        - **val**（脚本函数名称）
        
            指定一个与父元素关联的单个脚本子例程的名称。其使用取决于父 XML 元素的上下文。
            
            【示例：考虑以下表单字段属性的WordprocessingML片段：
            
            ```xml
            <w:ffData>
                <w:exitMacro w:val="HelloWorld" />
            </w:ffData>
            ```
            
            val 属性指定了在父元素上下文中必须使用名为 HelloWorld 的脚本函数；在这种情况下，在退出字段时执行。结束示例】
            
            The possible values for this attribute are defined by the ST_MacroName simple type ([§17.18.51]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MacroName) is located in §A.1. end note]

=== "英文"
    
    This element specifies a subroutine in a scripting language which should be executed when the when the run contents of the parent form field are exited. The language and location of this subroutine can be determined using any method desired by an application. [Note: It is at the discretion of an application to determine the scope and timing of "exiting" a form field, for example, when the user moves the insertion point in a user interface or upon each operation by an application without a user interface, etc. end note]
    
    If this element is omitted, then no subroutine shall be associated with exiting the run contents of the parent form field. If this element specifies a macro which cannot be located or is not supported by an application, then its value can be ignored, but shall not be lost upon resaving the file.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a form field:
    
    ```xml
    <w:ffData>
        <w:exitMacro w:val="TestExitFunction" />
    </w:ffData>
    ```
    
    The exitMacro element specifies that any application which processes this file should attempt to locate and execute a scripting subroutine called TestExitFunction when the contents of the form field are exited. If this subroutine cannot be located or executed, then this setting is silently ignored. end example]
    
    ??? abstract "Attributes"
        
        - **val** (Name of Script Function)
        
            Specifies the name of a single scripting subroutine which shall be associated with the parent element. Its use is specifies based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment for the properties of a form field:
            
            ```xml
            <w:ffData>
                <w:exitMacro w:val="HelloWorld" />
            </w:ffData>
            ```
            
            The val attribute specifies that a script function called HelloWorld must be used in the context of the parent element; in this case, to execute when the field is exited. end example]
            
            The possible values for this attribute are defined by the ST_MacroName simple type ([§17.18.51]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MacroName) is located in §A.1. end note]


## 17.16.17 ffData (表单字段属性)

**ffData (Form Field Properties)**

=== "中文"
    
    该元素指定了应与文档中的父表单字段关联的一组属性。此表单字段可以是以下任意一种类型（附带字段代码）：

    - 复选框（FORMCHECKBOX）
    - 下拉列表（FORMDROPDOWN）
    - 文本框（FORMTEXT）

    如果此元素存在，并且文档的字段代码没有指定其中一种类型的表单字段，则文档将被视为不符合规范。

    如果省略了此元素，则与父表单字段关联的属性将根据它们的默认值确定。

    【示例：考虑以下文本框表单字段的WordprocessingML片段：

    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:name w:val="TextTextBox" />
                <w:enabled w:val="false"/>
                <w:textInput>
                    <w:maxLength w:val="10" />
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```

    ffData 元素指定了此文本框表单字段的一组属性；在此示例中，通过 name 元素（[§17.16.27]）指定了一个名为 TestTextBox 的表单字段名称，通过 enabled 元素（[§17.16.14]）指定了禁用状态，并通过 maxLength 元素（[§17.16.26]）指定了最大字符长度为 10 个 Unicode 标量值。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFData) is located in §A.1. end note]

=== "英文"
    
    This element specifies a set of properties which shall be associated with the parent form field within the document. This form field can be of any of the following types (with the associated field codes in parentheses):
    
    - Checkbox (FORMCHECKBOX)
    - Drop-down List (FORMDROPDOWN)
    - Text box (FORMTEXT)
    
    If this element is present and the field codes for the document do not specify a form field of one of these types, then the document shall be considered non-conformant.
    
    If this element is omitted, then the properties associated with the parent form field shall be determined based on their default values.
    
    [Example: Consider the following WordprocessingML fragment for a text box form field:
    
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:name w:val="TextTextBox" />
                <w:enabled w:val="false"/>
                <w:textInput>
                    <w:maxLength w:val="10" />
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The ffData element specifies the set of properties for this text box form field; in this example, a form field name of TestTextBox via the name element ([§17.16.27]), a disabled state via the enabled element ([§17.16.14]), and a maximum character length of 10 Unicode scalar values via the maxLength element ([§17.16.26]). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFData) is located in §A.1. end note]

## 17.16.18 fldChar (复杂字段字符)

**fldChar (Complex Field Character)**

=== "中文"
    
    该元素指定了父运行中当前位置存在复杂字段字符。*复杂字段字符(complex field character)*是一种特殊字符，用于界定复杂字段的开始和结束，或者将其字段代码与当前字段结果分隔开来。
    
    通过使用两个必需的复杂字段字符来定义复杂字段：一个起始字符，指定文档内容中复杂字段的开始；以及一个结束字符，指定复杂字段的结束。此语法允许在文档中嵌套多个字段。
    
    此外，因为复杂字段可以在文档中同时指定其字段代码和当前结果，所以这两个项由可选的分隔符字符分隔开来，该字符定义了字段代码的结束和字段内容的开始。如果省略此字符，则表示字段的内容完全是字段代码（即，该字段没有结果）。
    
    【示例：考虑WordprocessingML文档中的以下复杂字段定义：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin" />
    </w:r>
    <w:r>
        <w:instrText>AUTHOR</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate" />
    </w:r>
    <w:r>
        <w:t>Rex Jaeschke</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end" />
    </w:r>
    ```
    
    这三个 fldChar 元素指定了：
    
    - 使用 type 属性值为 start 的字段的开始
    - 使用 type 属性值为 separate 的字段代码和当前字段结果之间的分隔符
    - 使用 type 属性值为 end 的字段的结束
    
    结束示例】
    
    如果复杂字段在文档段落结束之前没有关闭，则不会生成任何字段，并且每个独立的运行将被处理为不存在字段字符的情况（即，所有字段代码运行内容的内容将不会显示，并且字段结果将显示为文字）。
    
    【示例：考虑以下WordprocessingML文档：
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:fldChar w:fldCharType="begin" />
            </w:r>
            <w:r>
                <w:instrText>AUTHOR</w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate" />
            </w:r>
            <w:r>
                <w:t>Rex Jaeschke</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    由于主文档段落中不存在结束字符，因此复杂字段在技术上是不正确的。生成的内容必须解释为不存在字段字符的情况，因此文档中仅显示文本 Rex Jaeschke。结束示例】
    
    ??? abstract "Attributes"
        
        - **dirty**（字段结果无效）

            指定此字段已被应用程序标记，以指示其当前结果不再正确（陈旧），因为文档中进行了其他修改，并且在显示之前应更新这些内容，如果下一个处理应用程序支持此功能的话。

            [理由：此功能允许具有 ECMA-376 完整功能的有限子集的应用程序处理 Word Open XML 文档，而无需理解并根据其字段代码的语义更新所有字段。
            
            例如，一个应用程序可以添加一个新段落，并将目录标记为dirty，而无需了解如何重新计算该字段的内容。结束理由]
            
            如果省略了此属性，则应假定其值为 false。如果当前字段字符的类型不是 start，则可以忽略此设置。
            
            [示例：考虑以下复杂字段的WordprocessingML：
            
            ```xml
            …
            <w:r>
                <w:fldChar w:fldCharType="begin" w:dirty="true"/>
            </w:r>
            <w:r>
                <w:instrText>TOC /l 1-3</w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            …
            ```
            
            dirty 属性值为 true 指定该字段的内容不再基于文档内容是最新的，应当在具有此功能的应用程序读取文档时重新计算。结束示例]
            
            此属性的可能值由 ST_OnOff 简单类型（[§22.9.2.7]）定义。

        - **fldCharType**（字段字符类型）

            指定文档中当前复杂字段字符的类型。
                
            [示例：考虑以下复杂字段字符的WordprocessingML：
            
            ```xml
            …
            <w:fldChar w:fldCharType="separate" />
            …
            ```
            
            type 属性值为 separate 指定这是一个复杂字段的分隔符字符；因此，它用于在复杂字段中将字段代码与字段内容分隔开来。结束示例]
            
            此属性的可能值由 ST_FldCharType 简单类型（[§17.18.29]）定义。
        
        - **fldLock**（字段不应重新计算）

            指定父复杂字段不应重新计算其字段结果，即使应用程序尝试重新计算文档中所有字段的结果或明确请求重新计算也是如此。
            
            如果省略了此属性，则应假定其值为 false。如果当前字段字符的类型不是 start，则可以忽略此设置。
            
            [示例：考虑以下复杂字段的WordprocessingML：
            
            ```xml
            <w:r>
                <w:fldChar w:fldCharType="begin" w:fldLock="true"/>
            </w:r>
            …
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            <w:r>
                <w:t>字段结果</w:t>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="end" />
            </w:r>
            ```
            
            fldLock 属性值为 true 指定该字段的内容必须保持为字段结果，而不管当前字段代码的实际结果如何。结束示例]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FldChar) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a complex field character at the current location in the parent run. A *complex field character* is a special character which delimits the start and end of a complex field or separates its field codes from its current field result.
    
    A complex field is defined via the use of the two required complex field characters: a start character, which specifies the beginning of a complex field within the document content; and an end character, which specifies the end of a complex field. This syntax allows multiple fields to be embedded (or "nested") within each other in a document.
    
    As well, because a complex field can specify both its field codes and its current result within the document, these two items are separated by the optional separator character, which defines the end of the field codes and the beginning of the field contents. The omission of this character shall be used to specify that the contents of the field are entirely field codes (i.e. the field has no result).
    
    [Example: Consider the following complex field definition within a WordprocessingML document:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin" />
    </w:r>
    <w:r>
        <w:instrText>AUTHOR</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate" />
    </w:r>
    <w:r>
        <w:t>Rex Jaeschke</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end" />
    </w:r>
    ```
    
    The three fldChar elements specify:
    
    - The beginning of the field, using the type attribute value of start
    - The separator between the field codes and the current field results, using the type attribute value of separate
    - The end of the field, using the type attribute value of end
    
    end example]
    
    If a complex field is not closed before the end of a document story, then no field shall be generated and eac individual run shall be processed as if the field characters did not exist (i.e. the contents of all field code ru content shall not be displayed, and the field results shall be displayed as literal text).
    
    [Example: Consider the following WordprocessingML document:
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:fldChar w:fldCharType="begin" />
            </w:r>
            <w:r>
                <w:instrText>AUTHOR</w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate" />
            </w:r>
            <w:r>
                <w:t>Rex Jaeschke</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    The complex field is technically incorrect since no end character exists in the main document story. The resulting content must be interpreted as though no field characters exist, resulting in only the literal text Rex Jaeschke being displayed in the document. end example]
    
    ??? abstract "Attributes"
        
        - **dirty** (Field Result Invalidated)
        
            Specifies that this field has been flagged by an application to indicate that its current results are no longer correct (stale) due to other modifications made to the document, and these contents should be updated before they are displayed if this functionality is supported by the next processing application.
        
            [Rationale: This functionality allows applications with limited subsets of the full functionality of ECMA-376 to process Word Open XML documents without needing to understand and update all fields based on the semantics for their field codes.
            
            For example, an application can add a new paragraph and flag the table of contents as dirty, without needing to understand anything about how to recalculate that field's content. end rationale]
            
            If this attribute is omitted, then its value shall be assumed to be false. If the type of the current field character is not start, then his setting can be ignored.
            
            [Example: Consider the following WordprocessingML for a complex field:
            
            ```xml
            …
            <w:r>
                <w:fldChar w:fldCharType="begin" w:dirty="true"/>
            </w:r>
            <w:r>
                <w:instrText>TOC /l 1-3</w:instrText>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            …
            ```
            
            The dirty attribute value of true specifies that the contents of this field are no longer current based on the contents of the document, and should be recalculated whenever an application with this functionality reads the document. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
        
        - **fldCharType** (Field Character Type)
        
            Specifies the type of the current complex field character in the document.
                
            [Example: Consider the following WordprocessingML for a complex field character:
            
            ```xml
            …
            <w:fldChar w:fldCharType="separate" />
            …
            ```
            
            The type attribute value of separate specifies that this is a complex field separator character; therefore it is being used to separate the field codes from the field contents in a complex field. end example]
            
            The possible values for this attribute are defined by the ST_FldCharType simple type ([§17.18.29]).
        
        - **fldLock** (Field Should Not Be Recalculated)
        
            Specifies that the parent complex field shall not have its field result recalculated, even if an application attempts to recalculate the results of all fields in the document or a recalculation is explicitly requested.
            
            If this attribute is omitted, then its value shall be assumed to be false. If the type of the current field character is not start, then his setting can be ignored.
            
            [Example: Consider the following WordprocessingML for a complex field:
            
            ```xml
            <w:r>
                <w:fldChar w:fldCharType="begin" w:fldLock="true"/>
            </w:r>
            …
            <w:r>
                <w:fldChar w:fldCharType="separate"/>
            </w:r>
            <w:r>
                <w:t>field result</w:t>
            </w:r>
            <w:r>
                <w:fldChar w:fldCharType="end" />
            </w:r>
            ```
            
            The fldLock attribute value of true specifies that the contents of this field must remain field result regardless of the actual result of the current field codes. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FldChar) is located in §A.1. end note]

## 17.16.19 fldSimple (简单字段)

**fldSimple (Simple Field)**

=== "中文"
    
    该元素指定文档中当前位置存在简单字段。该字段的语义是通过其字段代码（[§17.16.5]）定义的。
    
    【示例：考虑以下简单字段的WordprocessingML片段：
    
    ```xml
    <w:fldSimple w:instr="FILENAME">
        <w:r>
            <w:t>Example Document.docx</w:t>
        </w:r>
    </w:fldSimple>
    ```
    
    fldSimple 元素使用简单字段语法定义了一个 FILENAME 字段（[§17.16.5.17]）。该字段的当前字段结果是 Example Document.docx。结束示例】
    
    ??? abstract "Attributes"
    
        - **dirty**（字段结果无效）

            指定该字段已被应用程序标记，以表示其当前结果不再正确（陈旧），因为文档中进行了其他修改，并且在显示之前应更新这些内容，如果下一个处理应用程序支持此功能的话。
            
            [理由：此功能允许具有 ECMA-376 完整功能的有限子集的应用程序处理 Word Open XML 文档，而无需理解并根据其字段代码的语义更新所有字段。
            
            例如，一个应用程序可以添加一个新段落，并将目录标记为 dirty，而无需了解如何重新计算该字段的内容。结束理由]
            
            如果省略了此属性，则应假定其值为 false。
            
            [示例：考虑以下简单字段的 WordprocessingML：
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:dirty="true"/>
            ```
            
            dirty 属性值为 true 指定该字段的内容不再基于文档内容是最新的，应当在具有此功能的应用程序读取文档时重新计算。结束示例]
            
            此属性的可能值由 ST_OnOff 简单类型（[§22.9.2.7]）定义。

        - **fldLock**（字段不应重新计算）

            指定父字段不应重新计算其字段结果，即使应用程序尝试重新计算文档中所有字段的结果或明确请求重新计算也是如此。
            
            如果省略了此属性，则应假定其值为 false。
            
            [示例：考虑以下简单字段的 WordprocessingML：
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:fldLock="true">
                <w:r>
                    <w:t>Rex Jaeschke</w:t>
                </w:r>
            </w:fldSimple>
            ```
            
            fldLock 属性值为 true 指定该字段的内容必须保持为 Rex Jaeschke，而不管当前字段代码的实际结果如何。结束示例]
            
            此属性的可能值由 ST_OnOff 简单类型（[§22.9.2.7]）定义。

        - **instr**（字段代码）

            指定简单字段的字段代码。可能的字段代码在 [§17.16.5] 中定义。
            
            [示例：考虑以下简单字段的 WordprocessingML：
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:fldLock="true">
                <w:r>
                    <w:t>Rex Jaeschke</w:t>
                </w:r>
            </w:fldSimple>
            ```
            
            instr 属性指定该简单字段的字段代码为 AUTHOR。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SimpleField) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a simple field at the current location in the document. The semantics of this field are defined via its field codes ([§17.16.5]).
    
    [Example: Consider the following WordprocessingML fragment for a simple field:
    
    ```xml
    <w:fldSimple w:instr="FILENAME">
        <w:r>
            <w:t>Example Document.docx</w:t>
        </w:r>
    </w:fldSimple>
    ```
    
    The fldSimple element defines a FILENAME field ([§17.16.5.17]) using the simple field syntax. The current field result for the field is Example Document.docx. end example]
    
    ??? abstract "Attributes"
    
        - **dirty** (Field Result Invalidated)
    
            Specifies that this field has been flagged by an application to indicate that its current results are no longer correct (stale) due to other modifications made to the document, and these contents should be updated before they are displayed if this functionality is supported by the next processing application.
            
            [Rationale: This functionality allows applications with limited subsets of the full functionality of ECMA-376 to process Word Open XML documents without needing to understand and update all fields based on the semantics for their field codes.
            
            For example, an application can add a new paragraph and flag the table of contents as dirty, without needing to understand anything about how to recalculate that field's content. end rationale]
            
            If this attribute is omitted, then its value shall be assumed to be false.
            
            [Example: Consider the following WordprocessingML for a simple field:
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:dirty="true"/>
            ```
            
            The dirty attribute value of true specifies that the contents of this field are no longer current based on the contents of the document, and should be recalculated whenever an application with this functionality reads the document. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
        - **fldLock** (Field Should Not Be Recalculated)
    
            Specifies that the parent field shall not have its field result recalculated, even if an application attempts to recalculate the results of all fields in the document or a recalculation is explicitly requested.
            
            If this attribute is omitted, then its value shall be assumed to be false.
            
            [Example: Consider the following WordprocessingML for a simple field:
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:fldLock="true">
                <w:r>
                    <w:t>Rex Jaeschke</w:t>
                </w:r>
            </w:fldSimple>
            ```
            
            The fldLock attribute value of true specifies that the contents of this field must remain Rex Jaeschke regardless of the actual result of the current field codes. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
        - **instr** (Field Codes)
    
            Specifies the field codes for the simple field. The possible field codes are defined in [§17.16.5].
            
            [Example: Consider the following WordprocessingML for a simple field:
            
            ```xml
            <w:fldSimple w:instr="AUTHOR" w:fldLock="true">
                <w:r>
                    <w:t>Rex Jaeschke</w:t>
                </w:r>
            </w:fldSimple>
            ```
            
            The instr attribute specifies the field codes for this simple field to be AUTHOR. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SimpleField) is located in §A.1. end note]

## 17.16.20 format (文本框表达字段格式)

**format (Text Box Form Field Formatting)**

=== "中文"
    
    该元素指定了在父表单字段内容被修改时应用于其内容的字段格式化。应用于字段的格式化类型取决于其类型元素（[§17.16.34]）的值，如下所示：
    
    - 当类型等于 currentDate、currentTime 或 date 时，使用 [§17.16.4.1] 中定义的日期格式化字符串。
    - 当类型等于 calculated 或 number 时，使用 [§17.16.4.2] 中定义的数字格式化字符串。
    - 当类型等于 regular 时，使用以下定义的文本格式化字符串：
    
    | **参数**      | **描述**                                                                   |
    | ------------- | -------------------------------------------------------------------------- |
    | UppercaseAll  | 所有字母均大写。[示例：Mary Smith 变为 MARY SMITH。结束示例]               |
    | LowercaseAll  | 所有字母均小写。[示例：Mary Smith 变为 mary smith。结束示例]               |
    | First capital | 使第一个单词的第一个字母大写。[示例：Mary Smith 变为 Mary smith。结束示例] |
    | Title case    | 使每个单词的第一个字母大写。[示例：Mary Smith 变为 Mary Smith。结束示例]   |
    
    [示例：考虑以下文本框表单字段属性的WordprocessingML片段：
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:type w:val="number" />
            <w:maxLength w:val="4" />
            <w:format w:val="0.00" />
        </w:textInput>
    </w:ffData>
    ```
    
    format 元素指定了应用于字段输入的字段格式化（在本例中，类型元素指定值为 number）。如果在该字段中输入了值为 8，则格式化后的结果将为 8.00。结束示例]
    
    ??? abstract "Attributes"
    
        - **val**（字符串值）

            指定其内容包含一个字符串。
            
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
            然而，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的字符串是最近的祖先结构化文档标记的标题。在每种情况下，该值在父元素的上下文中进行解释。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the field formatting which shall be applied to the contents of the parent form field whenever those contents are modified. The type of formatting which is applied to the field depends on the value of its type element ([§17.16.34]), as follows:
    
    - When the type is equal to currentDate, currentTime, or date, a date formatting string using the syntax defined in [§17.16.4.1]
    - When the type is equal to calculated or number, a number formatting string using the syntax defined in [§17.16.4.2]
    - When the type is equal to regular, a text formatting string defined as follows:
    
    | **Argument**  | **Description**                                                                                          |
    | ------------- | -------------------------------------------------------------------------------------------------------- |
    | UppercaseAll  | letters are uppercase. [Example: Mary Smith results in MARY SMITH. end example]                          |
    | LowercaseAll  | letters are lowercase. [Example: Mary Smith results in mary smith. end example]                          |
    | First capital | Capitalizes the first letter of the first word. [Example: Mary Smith results in Mary smith. end example] |
    | Title case    | Capitalizes the first letter of each word. [Example: Mary Smith results in Mary Smith. end example]      |
    
    [Example: Consider the following WordprocessingML fragment for the properties of a text box form field:
    
    ```xml
    <w:ffData>
    <w:textInput>
    <w:type w:val="number" />
    <w:maxLength w:val="4" />
    <w:format w:val="0.00" />
    </w:textInput>
    </w:ffData>
    ```
    
    The format element specifies the field formatting which is applied to the input to the field (in this case, a grouping of number formatting picture items as the type element specifies a value of number). If a value of 8 was entered into this field, the formatted result would be 8.00. end example]
    
    ??? abstract "Attributes"
    
        - **val** (String Value)
    
            Specifies that its contents contain a string.
            
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]


## 17.16.21 helpText (相关帮助文本)

**helpText (Associated Help Text)**

=== "中文"
    
    该元素指定了与父表单字段关联的可选帮助文本。ECMA-376未定义用于呈现此帮助文本的方法或用户界面。
    
    如果省略此元素，则不会与当前表单字段关联任何帮助文本。
    
    [示例：考虑以下用于下拉列表表单字段的WordprocessingML片段：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:helpText w:type="text" w:val="示例帮助文本。"/>
                <w:ddList>
                    …
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    helpText 元素指定了父表单字段的帮助文本 - 在本例中，是由字符串"示例帮助文本。"组成的文字帮助文本。结束示例]
    
    ??? abstract "Attributes"
    
        - **type**（帮助文本类型）

            指定此元素指定的帮助文本的类型，由下面的简单类型定义。
            
            如果省略此属性，则其值应假定为 text。
            
            [示例：考虑以下用于表单字段的WordprocessingML片段：
            
            ```xml
            <w:ffData>
                <w:helpText w:type="text" w:val="示例帮助文本。" />
            </w:ffData>
            ```
            
            type 属性的值为 text，指定了 val 属性中的文本是该表单字段的文字帮助文本。结束示例]
            
            此属性的可能值由ST_InfoTextType简单类型定义（[§17.18.43]）。

        - **val**（帮助文本值）

            指定当前表单字段的帮助文本。根据 type 属性的值，该字段的内容将如下解释：
            
            - 当 type 属性值为 text 时，包含表单字段的文字帮助文本。
            - 当 type 属性值为 autoText 时，包含包含表单字段帮助文本的词汇表文档条目的名称。
            
            [示例：考虑以下用于表单字段的WordprocessingML片段：
            
            ```xml
            <w:ffData>
                <w:helpText w:type="autoText" w:val="帮助文本" />
            </w:ffData>
            ```
            
            val 属性中的文本是包含该表单字段帮助文本的词汇表文档条目的名称，因为 type 属性的值为 autoText。结束示例]
            
            The possible values for this attribute are defined by the ST_FFHelpTextVal simple type ([§17.18.25]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFHelpText) is located in §A.1. end note]

=== "英文"
    
    This element specifies optional help text which shall be associated with the parent form field. The method or user interface by which this help text can be surfaced is not defined by ECMA-376.
    
    If this element is omitted, then no help text shall be associated with the current form field.
    
    [Example: Consider the following WordprocessingML fragment for a drop-down list form field:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:helpText w:type="text" w:val="Example help text."/>
                <w:ddList>
                    …
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The helpText element specifies the help text for the parent form field - in this case, literal help text consisting of the string Example help text. end example]
    
    ??? abstract "Attributes"
    
        - **type** (Help Text Type)
    
            Specifies the type of help text which is specified by this element, defined by the simple type below.
            
            If this attribute is omitted, then its value shall be assumed to be text.
            
            [Example: Consider the following WordprocessingML fragment for a form field:
            
            ```xml
            <w:ffData>
                <w:helpText w:type="text" w:val="Example help text." />
            </w:ffData>
            ```
            
            The type attribute has a value of text, which specifies that the text in the val attribute is the literal help text for this form field. end example]
            
            The possible values for this attribute are defined by the ST_InfoTextType simple type ([§17.18.43]).
    
        - **val** (Help Text Value)
    
            Specifies the help text for the current form field. Based on the value of the type attribute, the contents of this field shall be interpreted as follows:
            
            - When the type attribute value is text, contains the literal help text for the form field.
            - When the type attribute value is autoText, contains the name of a glossary document entry which contains the help text for the form field.
            
            [Example: Consider the following WordprocessingML fragment for a form field:
            
            ```xml
            <w:ffData>
                <w:helpText w:type="autoText" w:val="HelpText" />
            </w:ffData>
            ```
            
            The text in the val attribute is the name of a glossary document entry containing the help text for this form field, since the type attribute has a value of autoText. end example]
            
            The possible values for this attribute are defined by the ST_FFHelpTextVal simple type ([§17.18.25]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFHelpText) is located in §A.1. end note]

## 17.16.22 hyperlink (超链接)

**hyperlink (Hyperlink)**

=== "中文"
    
    这个元素指定了文档中当前位置的超链接存在。
    
    [示例：考虑以下用于超链接的WordprocessingML片段：
    
    ```xml
    <w:hyperlink r:id="rId10">
        <w:r>
            <w:t>点击这里</w:t>
        </w:r>
    </w:hyperlink>
    ```
    
    hyperlink 元素定义了一个超链接，其显示文本为“点击这里”，目标由与 Id 属性值为 rId10 的关系指定。结束示例]
    
    ??? abstract "Attributes"
    
        - **anchor**（超链接锚点）

            指定当前文档中一个书签的名称，该书签将成为此超链接的目标。

            如果省略此属性，则默认行为是导航到文档的开头。如果还使用 r:id 属性指定了超链接目标，则将忽略此属性。如果当前文档中不存在具有给定书签名称的书签，则默认行为是导航到文档的开头。
            
            [示例：考虑以下用于超链接的WordprocessingML片段：
            
            ```xml
            <w:hyperlink w:anchor="chapter3">
                <w:r>
                    <w:t>转到第三章</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            anchor 属性指定当前超链接的目标必须是文档中的书签 chapter3 中包含的文本。结束示例]
            
            此属性的可能值由 ST_String 简单类型（[§22.9.2.13]）定义。

        - **docLocation**（目标文档中的位置）

            指定目标文档中没有书签的位置。如何将此属性的内容链接到文档文本的方法不在 ECMA-376 的范围之内。
            
            如果省略此属性，则不会将任何位置与父超链接关联起来。
            
            如果还指定了 anchor 属性，则在调用超链接时可以忽略此属性。
            
            [示例：考虑以下用于超链接的WordprocessingML片段：
            
            ```xml
            <w:hyperlink r:id="rId9" w:docLocation="table">
                <w:r>
                    <w:t>点击此处</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            docLocation 属性指定当前超链接的目标必须是目标文档中由字符串 table 定位的区域。结束示例]
            
            此属性的可能值由 ST_String 简单类型（[§22.9.2.13]）定义。

        - **history**（添加到已查看超链接）

            指定当调用超链接时，父超链接的目标（通过 r:id 属性指定）是否应添加到已查看超链接列表中。
            
            如果省略此属性，则其值应假定为 false。
            
            [示例：考虑以下用于超链接的WordprocessingML片段：
            
            ```xml
            <w:hyperlink r:id="rId9" w:history="true">
                <w:r>
                    <w:t>http://www.example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            history 属性值为 true 指定调用文档内的当前超链接时，其目标必须添加到已访问超链接列表中。结束示例]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
        - **id**（超链接目标）

            命名空间：http://purl.oclc.org/ooxml/officeDocument/relationships

            指定关系的ID，其目标将用作此超链接的目标。
            
            如果省略此属性，则当前超链接没有外部超链接目标 - 仍然可以通过 anchor 属性在当前文档中定位。
            
            如果存在此属性，则应该优先于 anchor 属性中的值。
            
            [示例：考虑以下用于超链接的 WordprocessingML 片段：
            
            ```xml
            <w:hyperlink r:id="rId9">
                <w:r>
                    <w:t>http://www.example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            id 属性值 rId9 指定与相应 ID 属性值的关系部分项中的关系，在调用此超链接时应导航到该部分项。例如，如果关系部分项中存在以下 XML：
            
            ```xml
            <Relationships xmlns="…">
                <Relationship Id="rId9" Mode="External" Target=http://www.example.com />
            </Relationships>
            ```
            
            则此超链接的目标将是关系 rId9 的目标 - 在此示例中为 http://www.example.com。结束示例]
            
            此属性的可能值由 ST_RelationshipId 简单类型（[§22.8.2.1]）定义。

        - **tgtFrame**（超链接目标框架）

            指定父 HTML 框架集中父超链接的目标框架（如果存在）。此元素指定的所有值应处理如下：
            
            | 值          | 描述                                                                                                                                      |
            | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
            | _topOpen    | 将超链接目标显示在当前窗口的完整区域中。                                                                                                  |
            | _selfOpen   | 将超链接目标显示在超链接出现的同一框架中。                                                                                                |
            | _parentOpen | 将超链接目标显示在当前框架的父级中，或者如果此框架没有父级，则显示在当前框架中。                                                          |
            | _blankOpen  | 将超链接目标显示在新的 Web 浏览器窗口中。                                                                                                 |
            | 其他所有值  | 将超链接目标显示在具有指定名称的框架中。如果不存在具有此名称的框架，则在当前框架中打开。 </br> 如果此字符串不以字母字符开头，则将其忽略。 |
            
            如果省略此属性，则不会与父超链接关联任何目标框架信息。如果当前文档不是框架集的一部分，则可以忽略此信息。
            
            [示例：考虑以下用于超链接的 WordprocessingML 片段：
            
            ```xml
            <w:hyperlink r:id="rId9" w:tgtFrame="_top">
                <w:r>
                    <w:t>http://example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            tgtFrame 属性值 _top 指定此超链接的目标必须在当前窗口的完整区域中显示。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        - **tooltip**（关联字符串）

            指定一个字符串，可以在用户界面中显示为与父超链接相关联。此字符串由应用程序显示的方法不在 ECMA-376 的范围内。
            
            如果省略此属性，则在文档中不会将任何关联字符串链接到父超链接。
            
            [示例：考虑以下用于超链接的 WordprocessingML 片段：
            
            ```xml
            <w:hyperlink r:id="rId9" w:tooltip="点击这里！">
                <w:r>
                    <w:t>http://example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            tooltip 属性值指定父超链接具有关联字符串“点击这里！”，可以根据需要使用。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Hyperlink) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a hyperlink at the current location in the document.
    
    [Example: Consider the following WordprocessingML fragment for a hyperlink:
    
    ```xml
    <w:hyperlink r:id="rId10">
        <w:r>
            <w:t>Click here</w:t>
        </w:r>
    </w:hyperlink>
    ```
    
    The hyperlink element defines a hyperlink whose display text is Click here, and whose target is specified by the relationship with an Id attribute value of rId10. end example]
    
    ??? abstract "Attributes"
    
        - **anchor** (Hyperlink Anchor)
    
            Specifies the name of a bookmark in the current document which shall be the target of this hyperlink.
    
            If this attribute is omitted, then the default behavior shall be to navigate to the start of the document. If a hyperlink target is also specified using the r:id attribute, then this attribute shall be ignored. If no bookmark exists in the current document with the given bookmark name, then the default behavior shall be to navigate to the start of the document.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink w:anchor="chapter3">
                <w:r>
                    <w:t>Go to Chapter Three</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The anchor attribute specifies that the target of the current hyperlink must be the text contained within the bookmark chapter3 within the document. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        - **docLocation** (Location in Target Document)
    
            Specifies a location in the target of the hyperlink that has no bookmarks. The method by which the contents of this attribute are linked to document text is outside the scope of ECMA-376.
            
            If this attribute is omitted, then no location shall be associated with the parent hyperlink.
            
            If the anchor attribute is also specified, then this attribute can be ignored when the hyperlink is invoked.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink r:id="rId9" w:docLocation="table">
                <w:r>
                    <w:t>Click Here</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The docLocation attribute specifies that the target of the current hyperlink must be a region targeted by the string table within the target document. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        - **history** (Add To Viewed Hyperlinks)
    
            Specifies whether the target of the parent hyperlink (as specified via the r:id attribute) shall be added to a list of viewed hyperlinks when it is invoked.
            
            If this attribute is omitted, then its value shall be assumed to be false.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink r:id="rId9" w:history="true">
                <w:r>
                    <w:t>http://www.example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The history attribute value of true specifies that the target of the current hyperlink must be added to a list of visited hyperlinks when invoked within the document. end example] 
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
        - **id** (Hyperlink Target)
    
            Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
    
            Specifies the ID of the relationship whose target shall be used as the target for this hyperlink.
            
            If this attribute is omitted, then there shall be no external hyperlink target for the current hyperlink - a location in the current document can still be target via the anchor attribute.
            
            If this attribute exists, it shall supersede the value in the anchor attribute.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink r:id="rId9">
                <w:r>
                    <w:t>http://www.example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The id attribute value of rId9 specifies that relationship in the associated relationship part item with a corresponding Id attribute value must be navigated to when this hyperlink is invoked. For example, if the following XML is present in the associated relationship part item:
            
            ```xml
            <Relationships xmlns="…">
                <Relationship Id="rId9" Mode="External" Target=http://www.example.com />
            </Relationships>
            ```
            
            The target of this hyperlink would therefore be the target of relationship rId9 - in this case, http://www.example.com. end example]
            
            The possible values for this attribute are defined by the ST_RelationshipId simple type ([§22.8.2.1]).
    
        - **tgtFrame** (Hyperlink Target Frame)
    
            Specifies a frame within the parent HTML frameset for the target of the parent hyperlink when one exists. All values specified by this element shall be handled as follows:
            
            | Value            | Description                                                                                                                                                                                                      |
            | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
            | _topOpen         | hyperlink target in the full region of the current window.                                                                                                                                                       |
            | _selfOpen        | hyperlink target in the same frame as the hyperlink appears.                                                                                                                                                     |
            | _parentOpen      | hyperlink target in the parent of the current frame, or the current frame if this frame has no parent.                                                                                                           |
            | _blankOpen       | hyperlink target in a new web browser window.                                                                                                                                                                    |
            | all other values | Open hyperlink target in the frame with the specified name. If no frame exists with this name, open in the current frame. </br> If this string does not begin with an alphabetic character, it shall be ignored. |
            
            If this attribute is omitted, then no target frame information shall be associated with the parent hyperlink. If the current document is not part of a frameset, then this information can be ignored.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink r:id="rId9" w:tgtFrame="_top">
                <w:r>
                    <w:t>http://example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The tgtFrame attribute value of _top specifies that the target of this hyperlink must be displayed in the full extents of the current window. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        - **tooltip** (Associated String)
    
            Specifies a string which can be surfaced in a user interface as associated with the parent hyperlink. The method by which this string is surfaced by an application is outside the scope of ECMA-376.
            
            If this attribute is omitted, then no associated string shall be linked to the parent hyperlink in the document.
            
            [Example: Consider the following WordprocessingML fragment for a hyperlink:
            
            ```xml
            <w:hyperlink r:id="rId9" w:tooltip="Click here!">
                <w:r>
                    <w:t>http://example.com</w:t>
                </w:r>
            </w:hyperlink>
            ```
            
            The tooltip attribute value specifies that the parent hyperlink has the associated string of Click here!, which can be used as desired. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Hyperlink) is located in §A.1. end note]



## 17.16.23 instrText (字段代码)

**instrText (Field Code)**

=== "中文"
    
    这个元素指定该运行包含文档中复杂字段的字段代码（[§17.16.5]）。
    
    如果此元素包含在不属于复杂字段字段代码的运行中，则应将其及其内容视为常规文本。如果此元素包含在 del 元素内部，则文档不符合规范。
    
    [示例：考虑一个 WordprocessingML 中的复杂复选框字段。此字段将表示如下：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin" />
    </w:r>
    <w:r>
        <w:instrText>FORMCHECKBOX</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate" />
    </w:r>
    …
    <w:r>
        <w:fldChar w:fldCharType="end" />
    </w:r>
    ```
    
    字段代码包含在 instrText 节点中，该节点出现在复杂字段的字段代码部分中（即在分隔符字符之前）。结束示例]
    
    ??? abstract "属性"
    
        - **xml:space**（内容包含显著空格）
    
            命名空间：http://www.w3.org/XML/1998/namespace
    
            使用 W3C 空间保留规则指定应如何处理此元素的内容中的空白。
    
            [示例：考虑以下包含在 WordprocessingML 文档中的运行：
            
            ```xml
                <w:r>
                    <w:t> 显著空白     </w:t>
                </w:r>
            ```
            
            尽管文本内容两侧各有三个空格，但该空白未明确标记为显著，因此受当前指定的运行范围内的空间保留规则的约束。结束示例]
            
            此属性的可能值由 XML 1.0 规范的 §2.10 定义。
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Text) is located in §A.1. end note]

=== "英文"
    
    This element specifies that this run contains field codes ([§17.16.5]) within a complex field in the document.
    
    If this element is contained within a run which is not part of a complex field's field codes, then it and its contents should be treated as regular text. If this element is contained within a del element, then the document is non-conformant.
    
    [Example: Consider a complex checkbox field within a WordprocessingML. This field would be represented as follows:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin" />
    </w:r>
    <w:r>
        <w:instrText>FORMCHECKBOX</w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate" />
    </w:r>
    …
    <w:r>
        <w:fldChar w:fldCharType="end" />
    </w:r>
    ```
    
    The field code is contained in an instrText node which occurs within the field codes portion of the complex field (i.e. before the separator character). end example]
        
    ??? abstract "Attributes"
    
        - **xml:space** (Content Contains Significant Whitespace)
    
            Namespace: http://www.w3.org/XML/1998/namespace
    
            Specifies how white space should be handled for the contents of this element using the W3C space preservation rules.
    
            [Example: Consider the following run contained within a WordprocessingML document:
            
            ```xml
                <w:r>
                    <w:t> significant whitespace     </w:t>
                </w:r>
            ```
            
            Although there are three spaces on each side of the text content in the run, that whitespace has not been specifically marked as significant, therefore it is subject to the space preservation rules currently specified in that run's scope. end example]
            
            The possible values for this attribute are defined by §2.10 of the XML 1.0 specification.
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Text) is located in §A.1. end note]

## 17.16.24 label (表单字段label)

**label (Form Field Label)**

=== "中文"
    
    这个元素指定与当前表单字段关联的标签标识符。表示标签的标识符将存储在该元素的 val 属性上，并用于引用结构化文档标记的唯一标识符值。由特定唯一标识符解析的结构化文档标记的内容将用作引用该结构化文档标记的特定唯一标识符的表单字段的标签内容。如果存在多个标签元素实例，则所引用的标签按从最一般到最具体的顺序排序。[示例：用于指定国家名称的表单元素可能引用以下三个项目的标签（按顺序）：“发件人”、“家庭地址”和“国家”。结束示例]
    
    如果省略此元素或无法解析标签标识符的值，则不应将任何标签与给定的表单字段关联。
    
    [示例：考虑以下文本框表单字段，引用结构化文档标记作为标签：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>姓名</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:ffData>
        <w:name w:val="TextTextBox" />
        <w:enabled />
        <w:textInput />
        <w:label w:val="5" />
    </w:ffData>
    ```
    
    标签元素指定文本框表单字段使用标识符值为 5 的结构化文档标记的内容作为标签源。在此示例中，标签内容为“姓名”。结束示例]
    
    ??? abstract "属性"
    
        - **val**（十进制数值）
        
            指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下具有简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the label identifier associated with the current form field. The identifier representing the label shall be stored on this element’s val attribute and is used to reference the unique identifier value of a structured document tag. The contents of the structured document tag resolved by a specific unique identifier shall be used as the label content for the form field that references that specific unique identifier of the structured document tag. If multiple instances of the label element are present, the labels referenced are ordered from most general to most specific. [Example: A form element for specifying country name might reference the label for these three items (in order): “Sender”, “Home Address”, and “Country”. end example]
    
    If this element is omitted or the value of the label identifier cannot be resolved, then no label shall be associated with the given form field.
    
    [Example: Consider the following text box form field, which references a structured document tag as a label:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:ffData>
        <w:name w:val="TextTextBox" />
        <w:enabled />
        <w:textInput />
        <w:label w:val="5" />
    </w:ffData>
    ```
    
    The label element specifies that the text box form field uses the contents of the structured document tag with an identifier value of 5 as a label source. In this example, the label contents is “Name”. end example]
        
    ??? abstract "Attributes"
    
        - **val** (Decimal Number Value)
        
            Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.16.25 listEntry (下拉列表条目)

**listEntry (Drop-Down List Entry)**

=== "中文"
    
    这个元素指定文档中父下拉列表表单字段内的单个下拉列表项的存在。在 WordprocessingML 标记中 listEntry 元素序列的出现顺序将决定下拉列表在显示时的条目顺序。
    
    [示例：考虑下面的 WordprocessingML 片段，用于表示下拉列表表单字段的属性：
    
    ```xml
    <w:ffData>
        <w:ddList>
            <w:listEntry w:val="One" />
            <w:listEntry w:val="Two" />
            <w:listEntry w:val="Three" />
        </w:ddList>
    </w:ffData>
    ```
    
    这三个 listEntry 元素分别指定父下拉列表表单字段的一个下拉列表条目。在这种情况下，这些属性指定下拉列表在显示时必须按照 One、Two 和 Three 的顺序包含三个条目。结束示例]
    
    ??? abstract "属性"
    
        - **val**（字符串值）
        
            指定其内容包含一个字符串。
            
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
    
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，值都是根据父元素的上下文进行解释的。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a single drop-down list entry within the parent drop-down list form field in the document. The order of appearance of the series of listEntry elements in the WordprocessingML markup shall dictate the order of the entries in the drop-down list when it is displayed.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a drop-down list form field:
    
    ```xml
    <w:ffData>
        <w:ddList>
            <w:listEntry w:val="One" />
            <w:listEntry w:val="Two" />
            <w:listEntry w:val="Three" />
        </w:ddList>
    </w:ffData>
    ```
    
    The three listEntry elements each specify one drop-down list entry for the parent drop-down list form field. In this case, these properties specify that the drop-down list must contain three entries of One, Two, and Three in that order when displayed. end example]
    
    
    ??? abstract "Attributes"
    
        - **val** (String Value)
    
            Specifies that its contents contain a string.
            
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
    
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]


## 17.16.26 maxLength (文本框表单字段最大长度)

**maxLength (Text Box Form Field Maximum Length)**

=== "中文"
    
    这个元素指定在任何由 format 元素（[§17.16.20]）指定的格式化之前，父文本框表单字段内允许的文本的最大长度。如果文档加载时此字段的当前内容超过指定值，那么违规不会导致错误，但应用程序应阻止添加额外的字符，直到内容降低到该限制以下。
    
    如果省略此元素，则父文本框表单字段中的字符数不受限制。
    
    [示例：考虑下面的文本框表单字段属性的 WordprocessingML 片段：
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:type w:val="number" />
            <w:maxLength w:val="4" />
            <w:format w:val="0.00" />
        </w:textInput>
    </w:ffData>
    ```
    
    maxLength 元素指定，在应用程序编辑时，此表单字段的内容不得超过四个字符。结束示例]
    
    ??? abstract "属性"
    
        - **val**（十进制数值）
        
            指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下简单类型 ST_DecimalNumber 的数值 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须在父元素的上下文中解释。结束示例]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the maximum length of text which should be allowed within the parent text box form field before any formatting specified by the format element ([§17.16.20]). If the current contents of this field exceed the specified value when the document is loaded, that violation shall not result in an error, but the application shall prevent the addition of any additional characters until the contents are brought below that limit.
    
    If this element is omitted, then there shall be no limit on the number of characters in the parent text box form field.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a text box form field:
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:type w:val="number" />
            <w:maxLength w:val="4" />
            <w:format w:val="0.00" />
        </w:textInput>
    </w:ffData>
    ```
    
    The maxLength element specifies that the contents of this form field should not be allowed to exceed four characters when edited by an application. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Decimal Number Value)
        
            Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.16.27 name (表单字段名称)

**name (Form Field Name)**

=== "中文"
    
    这个元素指定当前表单字段的名称。
    
    [示例：考虑以下文本框表单字段的 WordprocessingML 片段：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:name w:val=”FirstName” />
                <w:textInput>
                    …
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    name 元素指定当前表单字段的名称为 FirstName。结束示例]
    
    ??? abstract "属性"
    
        - **val**（表单字段名称值）
    
            指定表单字段的名称。
            
            如果省略此属性，则父表单字段将没有名称。
            
            [示例：考虑以下表单字段的 WordprocessingML 片段：
            
            ```xml
            <w:ffData>
                <w:name w:val="ExampleFieldName"/>
            </w:ffData>
            ```
            
            val 属性指定当前表单字段的名称为 ExampleFieldName。结束示例]
            
            The possible values for this attribute are defined by the ST_FFName simple type ([§17.18.26]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFName) is located in §A.1. end note]

=== "英文"
    
    This element specifies the name of the current form field.
    
    [Example: Consider the following WordprocessingML fragment for a text box form field:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:name w:val=”FirstName” />
                <w:textInput>
                    …
                </w:textInput>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMTEXT </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="separate"/>
    </w:r>
    <w:r>
        <w:t>1</w:t>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The name element specifies that the name of the current form field is FirstName. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Form Field Name Value)
    
            Specifies the name of the form field.
            
            If this attribute is omitted, then the parent form field shall have no name.
            
            [Example: Consider the following WordprocessingML fragment for a form field:
            
            ```xml
            <w:ffData>
                <w:name w:val="ExampleFieldName"/>
            </w:ffData>
            ```
            
            The val attribute specifies that the name of the current form field is ExampleFieldName. end example]
            
            The possible values for this attribute are defined by the ST_FFName simple type ([§17.18.26]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFName) is located in §A.1. end note]

## 17.16.28 result (下拉列表选项)

**result (Drop-Down List Selection)**

=== "中文"
    
    这个元素指定了当前下拉列表表单字段中当前选定条目的零基索引。
    
    如果省略了这个元素，则当前下拉列表表单字段的选择应由 default 元素的值指定 ([§17.16.11])。如果属性值引用了不存在的索引值（即负数或超出下拉列表中项目数的数字），则可以忽略此值，并且当前下拉列表表单字段的选择应由 default 元素的值指定。
    
    [示例：考虑以下下拉列表表单字段的 WordprocessingML 片段：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:ddList>
                    <w:default w:val="1" />
                    <w:result w:val="2" />
                    <w:listEntry w:val="One" />
                    <w:listEntry w:val="Two" />
                    <w:listEntry w:val="Three" />
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    result 元素指定了当前下拉列表表单字段中当前选定的值的索引为 2。在这种情况下，生成的默认值文本为 Three。结束示例]
    
    ??? abstract "属性"
    
        - **val**（十进制数值）
        
            指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the zero-based index of the currently selected entry for the parent drop-down list form field.
    
    If this element is omitted, then the current drop-down list form field shall have the selection specified by the value of the default element ([§17.16.11]). If the attribute value references an index value which does not exist (i.e. a negative number or a number that exceeds the number of items in the drop-down list), then this value can be ignored and the current drop-down list form field shall have the selection specified by the value of the default element.
    
    [Example: Consider the following WordprocessingML fragment for a drop-down list form field:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:ddList>
                    <w:default w:val="1" />
                    <w:result w:val="2" />
                    <w:listEntry w:val="One" />
                    <w:listEntry w:val="Two" />
                    <w:listEntry w:val="Three" />
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The result element specifies the index of the currently selected value of the drop-down list form field to be 2. In this case, the resulting default value text is Three. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Decimal Number Value)
        
            Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.16.29 size (复选框表单字段大小)

**size (Checkbox Form Field Size)**

=== "中文"
    
    这个元素指定了父复选框表单字段的确切大小。结果字段将以此磅数显示，而不管通过样式层次结构在文档中对应内容的格式化指定了什么大小。
    
    [示例：考虑以下复选框表单字段属性的 WordprocessingML 片段：
    
    ```xml
    <w:ffData>
        <w:checkBox>
            <w:size w:val="20" />
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    size 元素指定复选框必须以十磅字体大小显示，而不管通过样式层次结构通常应用于此文本的格式化。结束示例]
    
    ??? abstract "属性"
    
        - **val**（半点测量）
    
            指定以半点（英寸的 1/144）为单位的正测量。
            
            此属性值的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <… w:val="30" />
            ```
            
            val 属性中的值为 30，相当于 15 磅（30 半点）。
            
            此值根据父元素的上下文进行解释。结束示例]
            
            The possible values for this attribute are defined by the ST_HpsMeasure simple type ([§17.18.42]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_HpsMeasure) is located in §A.1. end note]

=== "英文"
    
    This element specifies the exact size for the parent checkbox form field. The resulting field shall be displayed in this point size regardless of the size specified by the formatting of its corresponding content in the document via the style hierarchy.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a checkbox form field:
    
    ```xml
    <w:ffData>
        <w:checkBox>
            <w:size w:val="20" />
            <w:checked w:val="true" />
        </w:checkBox>
    </w:ffData>
    ```
    
    The size element specifies that the checkbox must be displayed in a ten point font size, regardless of the formatting which would normally be applied to this text via the style hierarchy. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Half Point Measurement)
    
            Specifies a positive measurement specified in half-points (1/144 of an inch).
            
            The contents of this attribute value are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <… w:val="30" />
            ```
            
            The value in the val attribute is 30, which is equivalent to 15 points (30 half-points). 
            
            This value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_HpsMeasure simple type ([§17.18.42]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_HpsMeasure) is located in §A.1. end note]

## 17.16.30 sizeAuto (自动调整表单字段的大小)

**sizeAuto (Automatically Size Form Field)**

=== "中文"
    
    这个元素指定父复选框表单字段应使用通过样式层次结构应用于其字段字符的磅数进行格式化。
    
    [示例：考虑以下复选框表单字段属性的 WordprocessingML 片段：
    
    ```xml
    <w:r>
        <w:rPr>
            <w:sz w:val="40"/>
        </w:rPr>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:checkBox>
                    <w:sizeAuto />
                    <w:checked w:val="true" />
                </w:checkBox>
            </w:ffData>
        </w:fldChar>
    </w:r>
    ```
    
    sizeAuto 元素指定复选框必须以通过样式层次结构通常应用于此文本的磅数大小显示。在本例中，这个大小是通过直接格式化在父运行上指定的二十磅。结束示例]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies that the parent checkbox form field shall be formatted using the point size which is applied to its field characters via the style hierarchy.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a checkbox form field:
    
    ```xml
    <w:r>
        <w:rPr>
            <w:sz w:val="40"/>
        </w:rPr>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:checkBox>
                    <w:sizeAuto />
                    <w:checked w:val="true" />
                </w:checkBox>
            </w:ffData>
        </w:fldChar>
    </w:r>
    ```
    
    The sizeAuto element specifies that the checkbox must be displayed in the point size of the formatting which would normally be applied to this text via the style hierarchy. In this case, this size is the twenty points specified via the direct formatting on the parent run. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

## 17.16.31 statusText (相关状态文本)

**statusText (Associated Status Text)**

=== "中文"
    
    这个元素指定了与父表单字段关联的可选状态文本。ECMA-376未定义此状态文本的呈现方法或用户界面。
    
    如果省略了此元素，则当前表单字段将不会关联任何状态文本。
    
    [示例：考虑以下用于下拉列表表单字段的 WordprocessingML 片段：
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:statusText w:type="text" w:val="示例状态文本。"/>
                <w:ddList>
                    …
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    statusText 元素指定了父表单字段的状态文本 - 在本例中，是由字符串“示例状态文本”组成的文本。结束示例]
    
    ??? abstract "属性"
    
        - **type**（状态文本类型）
    
            指定此元素指定的状态文本的类型，由下面的简单类型定义。
            
            如果省略了此属性，则其值应被假定为文本。
            
            [示例：考虑以下用于表单字段的 WordprocessingML 片段：
            
            ```xml
            <w:ffData>
                <w:statusText w:type="text" w:val="示例状态文本。" />
            </w:ffData>
            ```
            
            type 属性的值为 text，指定了 val 属性中的文本是此表单字段的字面状态文本。结束示例]
            
            此属性的可能值由 ST_InfoTextType 简单类型（[§17.18.43]）定义。
    
        - **val**（状态文本值）
    
            指定当前表单字段的状态文本。根据 type 属性的值，此字段的内容应解释如下：
            
            - 当 type 属性值为 text 时，包含表单字段的字面状态文本。
            - 当 type 属性值为 autoText 时，包含包含表单字段状态文本的术语表文档条目的名称。
            
            [示例：考虑以下用于表单字段的 WordprocessingML 片段：
            
            ```xml
            <w:ffData>
                <w:statusText w:type="autoText" w:val="MyStatusText" />
            </w:ffData>
            ```
            
            val 属性中的文本是包含此表单字段状态文本的术语表文档条目的名称，因为 type 属性的值为 autoText。结束示例]
            
            The possible values for this attribute are defined by the ST_FFStatusTextVal simple type ([§17.18.27]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFStatusText) is located in §A.1. end note]

=== "英文"
    
    This element specifies optional status text which shall be associated with the parent form field. The method or user interface by which this status text can be surfaced is not defined by ECMA-376.
    
    If this element is omitted, then no status text shall be associated with the current form field.
    
    [Example: Consider the following WordprocessingML fragment for a drop-down list form field:
    
    ```xml
    <w:r>
        <w:fldChar w:fldCharType="begin">
            <w:ffData>
                <w:statusText w:type="text" w:val="Example status text."/>
                <w:ddList>
                    …
                </w:ddList>
            </w:ffData>
        </w:fldChar>
    </w:r>
    <w:r>
        <w:instrText> FORMDROPDOWN </w:instrText>
    </w:r>
    <w:r>
        <w:fldChar w:fldCharType="end"/>
    </w:r>
    ```
    
    The statusText element specifies the status text for the parent form field - in this case, literal text consisting of the string Example status text. end example]
            
    ??? abstract "Attributes"
    
        - **type** (Status Text Type)
    
            Specifies the type of status text which is specified by this element, defined by the simple type below.
            
            If this attribute is omitted, then its value shall be assumed to be text.
            
            [Example: Consider the following WordprocessingML fragment for a form field:
            
            ```xml
            <w:ffData>
                <w:statusText w:type="text" w:val="Example status text." />
            </w:ffData>
            ```
            
            The type attribute has a value of text, which specifies that the text in the val attribute is the literal status text for this form field. end example]
            
            The possible values for this attribute are defined by the ST_InfoTextType simple type ([§17.18.43]).
    
        - **val** (Status Text Value)
    
            Specifies the status text for the current form field. Based on the value of the type attribute, the contents of this field shall be interpreted as follows:
            
            - When the type attribute value is text, contains the literal status text for the form field.
            - When the type attribute value is autoText, contains the name of a glossary document entry which contains the status text for the form field.
            
            [Example: Consider the following WordprocessingML fragment for a form field:
            
            ```xml
            <w:ffData>
                <w:statusText w:type="autoText" w:val="MyStatusText" />
            </w:ffData>
            ```
            
            The text in the val attribute is the name of a glossary document entry containing the status text for this form field, since the type attribute has a value of autoText. end example]
            
            The possible values for this attribute are defined by the ST_FFStatusTextVal simple type ([§17.18.27]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFStatusText) is located in §A.1. end note]

## 17.16.32 tabIndex (表单字段导航顺序索引)

**tabIndex (Form Field Navigation Order Index)**

=== "中文"
    
    这个元素指定了当前表单字段在文档中使用的导航（制表）顺序中的位置。
    
    制表索引将存储在此元素的 val 属性上，并类似于 HTML 中的 tabIndex 属性。
    
    支持制表索引的对象应由使用者按照以下顺序进行导航：
    
    - XML 指定了非零 tabIndex 值的对象首先导航。导航继续，从具有最低解析的 tabIndex 值的元素到具有最高解析的 tabIndex 值的元素。
    
        - 指定相同解析 tabIndex 值的对象按照它们在底层 WordprocessingML 中出现的词法顺序进行导航。
    
    - XML 没有指定索引或 XML 指定的解析 tabIndex 值为 0 的对象最后导航。这些对象按照它们在底层 WordprocessingML 中出现的词法顺序进行导航。
    
    [示例：考虑以下两个文本框表单字段，其中表单字段指定了一个制表索引：
    
    ```xml
    <w:ffData>
        <w:name w:val="FirstName" />
        <w:enabled />
        <w:textInput />
        <w:tabIndex w:val="1" />
    </w:ffData>
    …
    <w:ffData>
        <w:name w:val="LastName" />
        <w:enabled />
        <w:textInput />
        <w:tabIndex w:val="2" />
    </w:ffData>
    ```
    
    tabIndex 元素指定了 FirstName 表单字段必须是通过制表访问的第一个内容，而 LastName 表单字段必须是通过制表访问的第二个内容。结束示例]
    
    ??? abstract "属性"
    
        - **val**（正十进制数值）
        
            指定此属性的内容包含一个正十进制数。
            
            此正十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 ST_UnsignedDecimalNumber 类型的数值 WordprocessingML 属性：
        
            ```xml
            <… w:val="15" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例]
        
        The possible values for this attribute are defined by the ST_UnsignedDecimalNumber simple type ([§22.9.2.16]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_UnsignedDecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the position of the current form field in the navigation (tab) order used in the document.
    
    The tabbing index shall be stored on this element’s val attribute and is analogous to the tabIndex attribute in HTML.
    
    Objects that support tab index shall be navigated by consumers in the following order:
    
    - Objects for which the XML specifies a non-zero tabIndex value are navigated first. Navigation proceeds with the element with the lowest resolved value of tabIndex to the element with the highest resolved value of tabIndex.
        
        - Objects that specify identical resolved values of tabIndex is navigated in the lexical order in which the elements appear in the underlying WordprocessingML.
    
    - Objects for which the XML does not specify an index or objects for which the XML specifies a resolved tabIndex value of 0 are navigated last. These objects are navigated in the lexical order in which they appear in the underlying WordprocessingML.
    
    [Example: Consider the following two text box form fields where form field specifies a tab index:
    
    ```xml
    <w:ffData>
        <w:name w:val="FirstName" />
        <w:enabled />
        <w:textInput />
        <w:tabIndex w:val="1" />
    </w:ffData>
    …
    <w:ffData>
        <w:name w:val="LastName" />
        <w:enabled />
        <w:textInput />
        <w:tabIndex w:val="2" />
    </w:ffData>
    ```
    
    The tabIndex element specifies that the FirstName form field must be the first content to be reached via tabbing, whereas the LastName form field must be the second content to be reached via tabbing. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Positive Decimal Number Value)

            Specifies that the contents of this attribute contains a positive decimal number.
            
            The contents of this positive decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of type ST_UnsignedDecimalNumber:

            ```xml
            <… w:val="15" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
        
        The possible values for this attribute are defined by the ST_UnsignedDecimalNumber simple type ([§22.9.2.16]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_UnsignedDecimalNumber) is located in §A.1. end note]

## 17.16.33 textInput (文本框表单字段属性)

**textInput (Text Box Form Field Properties)**

=== "中文"

    这个元素指定了与文档中的父 FORMTEXT 文本框表单字段（[§17.16.5.22]）相关联的一组属性。
    
    如果父表单字段不是文本框（即其字段代码的值不是 FORMTEXT），那么这些属性可以被忽略。
    
    [示例：考虑以下用于文本框表单字段属性的 WordprocessingML 片段：
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:maxLength w:val="4" />
            …
            <w:type w:val="number" />
        </w:textInput>
    </w:ffData>
    ```
    
    textInput 元素指定它包含了父文本框表单字段的一组属性。在这种情况下，这些属性通过 maxLength 元素（[§17.16.26]）指定了下拉列表的内容不能超过四个字符，并且通过 type 元素（[§17.16.34]）指定了它的内容必须是一个数字。
    
    结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFTextInput) is located in §A.1. end note]

=== "英文"

    This element specifies a set of properties which shall be associated with the parent FORMTEXT text box form field ([§17.16.5.22]) within the document.
    
    If the parent form field is not a text box (i.e. its field code does not have a value of FORMTEXT), then these properties can be ignored.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a text box form field:
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:maxLength w:val="4" />
            …
            <w:type w:val="number" />
        </w:textInput>
    </w:ffData>
    ```
    
    The textInput element specifies that it contains a set of properties for the parent text box form field. In this case, these properties specify that the drop-down list must contain no more than four characters via the maxLength element ([§17.16.26]), and that its contents must contain a number via the type element ([§17.16.34]).
    
    end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFTextInput) is located in §A.1. end note]

## 17.16.34 type (文本框表单字段类型)

**type (Text Box Form Field Type)**

=== "中文"

    这个元素指定了当前文本框表单字段内容的类型。该元素不应该用于阻止字段中任何内容的成功加载，但应该用于解析 format 元素（[§17.16.20]）中指定的格式，并在编辑应用程序的内容时防止添加非法内容。
    
    如果省略了这个元素，则应假定其默认值为 regular。
    
    [示例：考虑以下用于文本框表单字段属性的 WordprocessingML 片段：
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:type w:val="number" />
            <w:maxLength w:val="4" />
            <w:format w:val="0.00" />
        </w:textInput>
    </w:ffData>
    ```
    
    type 元素指定了应用程序处理此表单字段内容时应将其视为数字。结束示例]
    
    ??? abstract "属性"
    
        - **val**（文本框表单字段类型值）
    
            指定文本框表单字段的类型，如下面引用的简单类型所定义。
    
            [示例：考虑以下用于文本框表单字段属性的 WordprocessingML 片段：
            
            ```xml
            <w:ffData>
                <w:textInput>
                    <w:type w:val="currentDate" />
                </w:textInput>
            </w:ffData>
            ```
            
            currentDate 的 val 属性值指定了在更新字段时，该表单字段的内容应为当前日期。结束示例]
            
            The possible values for this attribute are defined by the ST_FFTextType simple type ([§17.18.28]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFTextType) is located in §A.1. end note]

=== "英文"

    This element specifies the type of the contents of the current text box form field. This element shall not be used to prevent the successful loading of any contents in the field, but shall be used to parse the formatting specified in the format element ([§17.16.20]) and should be used to prevent the addition of illegal content when its contents are edited by an application.
    
    If this element is omitted, then its default value shall be assumed to be regular.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a text box form field:
    
    ```xml
    <w:ffData>
        <w:textInput>
            <w:type w:val="number" />
            <w:maxLength w:val="4" />
            <w:format w:val="0.00" />
        </w:textInput>
    </w:ffData>
    ```
    
    The type element specifies that the contents of this form field should be handled as a number by an application. end example]
            
    ??? abstract "Attributes"
    
        - **val** (Text Box Form Field Type Values)
    
            Specifies the type of the text box form field, as defined by the simple type referenced below.
    
            [Example: Consider the following WordprocessingML fragment for the properties of a text box form field:
            
            ```xml
            <w:ffData>
                <w:textInput>
                    <w:type w:val="currentDate" />
                </w:textInput>
            </w:ffData>
            ```
            
            The val attribute value of currentDate specifies that the contents of this form field should be the current date when the field is updated. end example]
            
            The possible values for this attribute are defined by the ST_FFTextType simple type ([§17.18.28]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_FFTextType) is located in §A.1. end note]

[§17.16.1]: #17161-语法
[§17.16.2]: #17162-xml表示
[§17.16.3]: #17163-公式和表达式
[§17.16.3.1]: #171631-常量
[§17.16.3.2]: #171632-书签
[§17.16.3.3]: #171633-运算
[§17.16.3.4]: #171634-函数
[§17.16.3.5]: #171635-表格单元格引用
[§17.16.4]: #17164-字段格式
[§17.16.4.1]: #171641-日期和时间格式
[§17.16.4.2]: #171642-数字格式
[§17.16.4.3]: #171643-一般格式
[§17.16.4.3.1]: #1716431-一般格式---数值
[§17.16.4.3.2]: #1716432-一般格式---字符串值
[§17.16.4.3.3]: #1716433-一般格式---字段结果格式
[§17.16.5]: #17165-字段定义
[§17.16.5.1]: #171651-地址块addressblock
[§17.16.5.2]: #171652-前进advance
[§17.16.5.3]: #171653-询问ask
[§17.16.5.4]: #171654-作者author
[§17.16.5.5]: #171655-自动文本autotext
[§17.16.5.6]: #171656-自动文本列表autotextlist
[§17.16.5.7]: #171657-参考目录bibliography
[§17.16.5.8]: #171658-引文citation
[§17.16.5.9]: #171659-注释comments
[§17.16.5.10]: #1716510-比较compare
[§17.16.5.11]: #1716511-创建日期createdate
[§17.16.5.12]: #1716512-数据库database
[§17.16.5.13]: #1716513-日期date
[§17.16.5.14]: #1716514-文档属性docproperty
[§17.16.5.15]: #1716515-文档变量docvariable
[§17.16.5.16]: #1716516-编辑时间edittime
[§17.16.5.17]: #1716517-文件名filename
[§17.16.5.18]: #1716518-文件大小filesize
[§17.16.5.19]: #1716519-填写fillin
[§17.16.5.20]: #1716520-表单复选框formcheckbox
[§17.16.5.21]: #1716521-表单下拉菜单formdropdown
[§17.16.5.22]: #1716522-表格文本formtext
[§17.16.5.23]: #1716523-转到按钮gotobutton
[§17.16.5.24]: #1716524-问候语greetingline
[§17.16.5.25]: #1716525-超链接hyperlink
[§17.16.5.26]: #1716526-如果if
[§17.16.5.27]: #1716527-包含图片includepicture
[§17.16.5.28]: #1716528-包含文本includetext
[§17.16.5.29]: #1716529-索引index
[§17.16.5.30]: #1716530-关键词keywords
[§17.16.5.31]: #1716531-最后保存者lastsavedby
[§17.16.5.32]: #1716532-链接link
[§17.16.5.33]: #1716533-列表编号listnum
[§17.16.5.34]: #1716534-宏按钮macrobutton
[§17.16.5.35]: #1716535-合并字段mergefield
[§17.16.5.36]: #1716536-合并记录mergerec
[§17.16.5.37]: #1716537-合并序列mergeseq
[§17.16.5.38]: #1716538-下一个next
[§17.16.5.39]: #1716539-下一个如果nextif
[§17.16.5.40]: #1716540-注意参考noteref
[§17.16.5.41]: #1716541-字符数numchars
[§17.16.5.42]: #1716542-页数numpages
[§17.16.5.43]: #1716543-词数numwords
[§17.16.5.44]: #1716544-页page
[§17.16.5.45]: #1716545-页面参考pageref
[§17.16.5.46]: #1716546-打印print
[§17.16.5.47]: #1716547-打印日期printdate
[§17.16.5.48]: #1716548-私有private
[§17.16.5.49]: #1716549-引用quote
[§17.16.5.50]: #1716550-rdrd
[§17.16.5.51]: #1716551-引用ref
[§17.16.5.52]: #1716552-版本号revnum
[§17.16.5.53]: #1716553-保存日期savedate
[§17.16.5.54]: #1716554-节section
[§17.16.5.55]: #1716555-节页面sectionpages
[§17.16.5.56]: #1716556-序列seq
[§17.16.5.57]: #1716557-集合set
[§17.16.5.58]: #1716558-跳过如果skipif
[§17.16.5.59]: #1716559-样式引用styleref
[§17.16.5.60]: #1716560-主题subject
[§17.16.5.61]: #1716561-符号symbol
[§17.16.5.62]: #1716562-tata
[§17.16.5.63]: #1716563-tctc
[§17.16.5.64]: #1716564-模板template
[§17.16.5.65]: #1716565-时间time
[§17.16.5.66]: #1716566-title
[§17.16.5.67]: #1716567-标题toa
[§17.16.5.68]: #1716568-目录toc
[§17.16.5.69]: #1716569-用户地址useraddress
[§17.16.5.70]: #1716570-用户姓名缩写userinitials
[§17.16.5.71]: #1716571-用户名username
[§17.16.5.72]: #1716572-xexe
[§17.16.6]: #17166-calconexit-当前字段修改时重新计算字段
[§17.16.7]: #17167-checkbox-复选框表单字段属性
[§17.16.8]: #17168-checked-复选框表单字段状态
[§17.16.9]: #17169-ddlist-下拉列表表单字段属性
[§17.16.10]: #171610-default-默认文本框表单字段字符串
[§17.16.11]: #171611-default-默认下拉列表项目索引
[§17.16.12]: #171612-default-默认复选框表单字段状态
[§17.16.13]: #171613-delinstrtext-删除的字段代码
[§17.16.14]: #171614-enabled-启用表单字段
[§17.16.15]: #171615-entrymacro-在表单字段输入上执行的脚本函数
[§17.16.16]: #171616-exitmacro-在表单字段退出时执行的脚本函数
[§17.16.17]: #171617-ffdata-表单字段属性
[§17.16.18]: #171618-fldchar-复杂字段字符
[§17.16.19]: #171619-fldsimple-简单字段
[§17.16.20]: #171620-format-文本框表达字段格式
[§17.16.21]: #171621-helptext-相关帮助文本
[§17.16.22]: #171622-hyperlink-超链接
[§17.16.23]: #171623-instrtext-字段代码
[§17.16.24]: #171624-label-表单字段label
[§17.16.25]: #171625-listentry-下拉列表条目
[§17.16.26]: #171626-maxlength-文本框表单字段最大长度
[§17.16.27]: #171627-name-表单字段名称
[§17.16.28]: #171628-result-下拉列表选项
[§17.16.29]: #171629-size-复选框表单字段大小
[§17.16.30]: #171630-sizeauto-自动调整表单字段的大小
[§17.16.31]: #171631-statustext-相关状态文本
[§17.16.32]: #171632-tabindex-表单字段导航顺序索引
[§17.16.33]: #171633-textinput-文本框表单字段属性
[§17.16.34]: #171634-type-文本框表单字段类型

[§17.3.1.20]: ./03paragraphs.md#173120-outlinelvl-相关大纲级别

[§17.13.5.14]: ./13annotations.md#1713514-del-删除运行内容

[§17.14]: ./14mailmerge.md

[§17.15.1.56]: ./15settings.md#1715156-listseparator-用于字段代码评估的列表分隔符

[§17.16]: ./16fields.md

[§17.17.4]: ./17miscellaneous.md#17174-布尔属性-ct_onoff

[§17.18.10]: ./18simpletypes.md#171810-st_decimalnumber-十进制数值
[§17.18.25]: ./18simpletypes.md#171825-st_ffhelptextval-帮助文本值
[§17.18.26]: ./18simpletypes.md#171826-st_ffname-表单字段名称值
[§17.18.27]: ./18simpletypes.md#171827-st_ffstatustextval-状态文本值
[§17.18.28]: ./18simpletypes.md#171828-st_fftexttype-文本框表单字段类型值
[§17.18.29]: ./18simpletypes.md#171829-st_fldchartype-复杂字段字符类型
[§17.18.42]: ./18simpletypes.md#171842-st_hpsmeasure-以半点测量
[§17.18.43]: ./18simpletypes.md#171843-st_infotexttype-帮助或状态文本类型
[§17.18.51]: ./18simpletypes.md#171851-st_macroname-脚本子例程名称值

[§22.8.2.1]: ../chapter22/officedocumentrelationships.md#22821-st_relationshipid-显式关系-id

[§22.9.2.7]: ../chapter22/sharedsimpletypes.md#22927-st_onoff-开关值
[§22.9.2.13]: ../chapter22/sharedsimpletypes.md#229213-st_string-字符串
[§22.9.2.16]: ../chapter22/sharedsimpletypes.md#229216-st_unsigneddecimalnumber-无符号十进制数值
