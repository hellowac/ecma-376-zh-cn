# 22.9 Shared Simple Types

=== "中文"

    以下简单类型代表整个 Office Open XML 中使用的常见值格式，并且已进行集中处理以确保其用法保持一致。

=== "英文"

    The following simple types represent common value formats used throughout Office Open XML, and have been centralized in order to ensure their usage remains consistent.

## 22.9.1 目录

=== "中文"

    - [22.9.2 简单类型](#2292-简单类型)
        - [22.9.2.1 ST\_CalendarType (日历类型)](#22921-st_calendartype-日历类型)
        - [22.9.2.2 ST\_ConformanceClass (文档一致性等级值)](#22922-st_conformanceclass-文档一致性等级值)
        - [22.9.2.3 ST\_FixedPercentage (带符号的固定百分比值)](#22923-st_fixedpercentage-带符号的固定百分比值)
        - [22.9.2.4 ST\_Guid (128-Bit GUID)](#22924-st_guid-128-bit-guid)
        - [22.9.2.5 ST\_HexColorRGB (十六进制颜色值)](#22925-st_hexcolorrgb-十六进制颜色值)
        - [22.9.2.6 ST\_Lang (语言参考)](#22926-st_lang-语言参考)
        - [22.9.2.7 ST\_OnOff (开/关值)](#22927-st_onoff-开关值)
        - [22.9.2.8 ST\_Panose (Panose-1整数)](#22928-st_panose-panose-1整数)
        - [22.9.2.9 ST\_Percentage (带符号的百分比值)](#22929-st_percentage-带符号的百分比值)
        - [22.9.2.10 ST\_PositiveFixedPercentage (带符号的正固定百分比值)](#229210-st_positivefixedpercentage-带符号的正固定百分比值)
        - [22.9.2.11 ST\_PositivePercentage (带符号的正百分比值)](#229211-st_positivepercentage-带符号的正百分比值)
        - [22.9.2.12 ST\_PositiveUniversalMeasure (积极的普遍测量)](#229212-st_positiveuniversalmeasure-积极的普遍测量)
        - [22.9.2.13 ST\_String (字符串)](#229213-st_string-字符串)
        - [22.9.2.14 ST\_TwipsMeasure (以二十分之一点为单位的测量)](#229214-st_twipsmeasure-以二十分之一点为单位的测量)
        - [22.9.2.15 ST\_UniversalMeasure (通用测量)](#229215-st_universalmeasure-通用测量)
        - [22.9.2.16 ST\_UnsignedDecimalNumber (无符号十进制数值)](#229216-st_unsigneddecimalnumber-无符号十进制数值)
        - [22.9.2.17 ST\_VerticalAlignRun (垂直定位位置)](#229217-st_verticalalignrun-垂直定位位置)
        - [22.9.2.18 ST\_XAlign (水平对齐位置)](#229218-st_xalign-水平对齐位置)
        - [22.9.2.19 ST\_Xstring (转义字符串)](#229219-st_xstring-转义字符串)
        - [22.9.2.20 ST\_YAlign (垂直对齐位置)](#229220-st_yalign-垂直对齐位置)
        - [22.9.2.21 ST\_XmlName (XML 名称)](#229221-st_xmlname-xml-名称)

=== "英文"

    **Table of Contents**

    **This subclause is informative.**

    - 22.9.2 Simple Types
        - 22.9.2.1 ST_CalendarType (Calendar Types)
        - 22.9.2.2 ST_ConformanceClass (Document Conformance Class Value)
        - 22.9.2.3 ST_FixedPercentage (Fixed Percentage Value with Sign)
        - 22.9.2.4 ST_Guid (128-Bit GUID)
        - 22.9.2.5 ST_HexColorRGB (Hexadecimal Color Value)
        - 22.9.2.6 ST_Lang (Language Reference)
        - 22.9.2.7 ST_OnOff (On/Off Value)
        - 22.9.2.8 ST_Panose (Panose-1 Number)
        - 22.9.2.9 ST_Percentage (Percentage Value with Sign)
        - 22.9.2.10 ST_PositiveFixedPercentage (Positive Fixed Percentage Value with Sign)
        - 22.9.2.11 ST_PositivePercentage (Positive Percentage Value with Sign)
        - 22.9.2.12 ST_PositiveUniversalMeasure (Positive Universal Measurement)
        - 22.9.2.13 ST_String (String)
        - 22.9.2.14 ST_TwipsMeasure (Measurement in Twentieths of a Point)
        - 22.9.2.15 ST_UniversalMeasure (Universal Measurement)
        - 22.9.2.16 ST_UnsignedDecimalNumber (Unsigned Decimal Number Value)
        - 22.9.2.17 ST_VerticalAlignRun (Vertical Positioning Location)
        - 22.9.2.18 ST_XAlign (Horizontal Alignment Location)
        - 22.9.2.19 ST_Xstring (Escaped String)
        - 22.9.2.20 ST_YAlign (Vertical Alignment Location)
        - 22.9.2.21 ST_XmlName (XML Name)

## 22.9.2 简单类型

=== "中文"

    这是专用于共享简单类型的简单类型的完整列表。

=== "英文"

    **Simple Types**

    This is the complete list of simple types dedicated to Shared Simple Types.

### 22.9.2.1 ST_CalendarType (日历类型)

=== "中文"

    此简单类型指定可在 Office Open XML 文档上下文中使用的可能的日历类型。

    ??? info "Example"

        考虑以下结构化文档标签属性：

        ```xml
        <w:sdtPr>
            <w:date w:fullDate="2006-01-01T06:30:00Z">
                <w:calendar w:val="gregorian"/>
            </w:date>
        </w:sdtPr>
        ```

        Calendar 元素指定可以在文档中显示的日历的日历类型必须是公历格式（gregorian）。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：

    ??? abstract "枚举"

        **gregorian** (公历/Gregorian)

        :   指定应使用 ISO 8601 中定义的公历。 该日历应本地化为适当的语言

        **gregorianArabic** (公历阿拉伯历/Gregorian Arabic Calendar) 

        :   指定应使用 ISO 8601 中定义的公历。
            
            该日历的值应以阿拉伯语显示。

        **gregorianMeFrench** (公历中东法国日历/Gregorian Middle East French Calendar)

        :   指定应使用 ISO 8601 中定义的公历。

            The values for this calendar should be presented in Middle East French.

        **gregorianUs** (公历英语日历/Gregorian English Calendar)

        :   指定应使用 ISO 8601 中定义的公历。

            该日历的值应以英语显示。

        **gregorianXlitEnglish** (公历音译英语/Gregorian Transliterated English)

        :   指定应使用 ISO 8601 中定义的公历。

            该日历的值应该是相应阿拉伯字符中英文字符串的表示形式（公历英文的阿拉伯音译）。

        **gregorianXlitFrench** (格里高利音译法文/Gregorian Transliterated French) 

        :   指定应使用 ISO 8601 中定义的公历。

            此日历的值应该是相应阿拉伯字符中法语字符串的表示形式（公历法语的阿拉伯音译）。

        **hebrew** (希伯来语/Hebrew)

        :   指定应使用希伯来阴历，如逾越节 [Har'El, Zvi] 的高斯公式和口述律法完整重述 (Mishneh Torah) 所描述的那样。

        **hijri** (回历/Hijri) 

        :   规定应使用沙特阿拉伯王国、伊斯兰事务部、捐赠、宣教和指南所规定的回历农历。

        **japan** (日本天皇时代/Japanese Emperor Era)

        :   指定应使用日本工业标准 JIS X 0301 中描述的日本天皇纪元日历。

        **korea** (朝鲜檀君时代/Korean Tangun Era)

        :   规定应使用韩国第 4 号法律法令所述的韩国檀君纪元日历。

        **none** (无日历类型/No Calendar Type) 

        :   指定不应使用日历。

        **saka** (坂艾拉/Saka Era)

        :   指定应使用印度日历改革委员会所描述的萨卡时代日历，作为印度星历和航海年历的一部分。

        **taiwan** (台湾/Taiwan)

        :   指定应使用中国国家标准 CNS 7648 定义的台湾历。

        **thai** (泰国/Thai) 

        :   指定由 H.M. 皇家法令定义的泰历。 国王 Vajiravudh（拉玛六世）在皇家公报 B.E. 2456（公元 1913 年）和首相 Phibunsongkhram（公元 1941 年）的法令中，以公历 1 月 1 日开始年份，并将零年映射到公历公元前 543 年，应使用 。

    [Note: 此简单类型的内容模型 (ST_CalendarType) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_CalendarType (Calendar Types)**

    This simple type specifies the possible types of calendars which can be used within the context of an Office Open XML document.

    ??? info "Example"

        Consider the following structured document tag properties:

        ```xml
        <w:sdtPr>
            <w:date w:fullDate="2006-01-01T06:30:00Z">
                <w:calendar w:val="gregorian"/>
            </w:date>
        </w:sdtPr>
        ```

        The calendar element specifies that the calendar type for a calendar which can be displayed in the document must be the Gregorian calendar format (gregorian).

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        **gregorian** (Gregorian)

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used. This calendar should be localized into the appropriate language

        **gregorianArabic** (Gregorian Arabic Calendar) 

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used.
            
            The values for this calendar should be presented in Arabic.

        **gregorianMeFrench** (Gregorian Middle East French Calendar)

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used.

            The values for this calendar should be presented in Middle East French.

        **gregorianUs** (Gregorian English Calendar)

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used.

            The values for this calendar should be presented in English.

        **gregorianXlitEnglish** (Gregorian Transliterated English)

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used.

            The values for this calendar should be the representation of the English strings in the corresponding Arabic characters (the Arabic transliteration of the English for the Gregorian calendar).

        gregorianXlitFrench (Gregorian Transliterated French) 

        :   Specifies that the Gregorian calendar, as defined in ISO 8601, shall be used.

            The values for this calendar should be the representation of the French strings in the corresponding Arabic characters (the Arabic transliteration of the French for the Gregorian calendar).

        hebrew (Hebrew)

        :   Specifies that the Hebrew lunar calendar, as described by the Gauss formula for Passover [Har'El, Zvi] and The Complete Restatement of Oral Law (Mishneh Torah), shall be used.

        hijri (Hijri) 

        :   Specifies that the Hijri lunar calendar, as described by the Kingdom of Saudi Arabia, Ministry of Islamic Affairs, Endowments, Da‘wah and Guidance, shall be used.

        japan (Japanese Emperor Era)

        :   Specifies that the Japanese Emperor Era calendar, as described by Japanese Industrial Standard JIS X 0301, shall be used.

        korea (Korean Tangun Era)

        :   Specifies that the Korean Tangun Era calendar, as described by Korean Law Enactment No. 4, shall be used.

        none (No Calendar Type) 

        :   Specifies that no calendar should be used.

        saka (Saka Era)

        :   Specifies that the Saka Era calendar, as described by the Calendar Reform Committee of India, as part of the Indian Ephemeris and Nautical Almanac, shall be used.

        taiwan (Taiwan)

        :   Specifies that the Taiwanese calendar, as defined by the Chinese National Standard CNS 7648, shall be used.

        thai (Thai) 

        :   Specifies that the Thai calendar, as defined by the Royal Decree of H.M. King Vajiravudh (Rama VI) in Royal Gazette B. E. 2456 (1913 A.D.) and by the decree of Prime Minister Phibunsongkhram (1941 A.D.) to start the year on the Gregorian January 1 and to map year zero to Gregorian year 543 B.C., shall be used.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_CalendarType) is located in §A.6.9. end note]

### 22.9.2.2 ST_ConformanceClass (文档一致性等级值)

=== "中文"

    此简单类型指定特定 Office Open XML 文档所遵循的一致性类别.
    
    ??? info "Example"

        考虑以下 SpreadsheetML Workbook 部分标记：

        ```xml
        <workbook … conformance="transitional">
         …
        </workbook>
        ```

        该SpreadsheetML 文档的一致性属性值为transitional，因此它符合SML Transitional 一致性类。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：

    ??? abstract "枚举"

        **strict** (Office Open XML Strict) 

        :   指定文档符合 Office Open XML 严格(Strict) 模式。

        **transitional** (Office Open XML Transitional)

        :   指定文档符合 Office Open XML 过渡(Transitional) 模式。

    [Note: 此简单类型的内容模型 (ST_ConformanceClass) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_ConformanceClass (Document Conformance Class Value)**

    This simple type specifies the conformance class to which a particular Office Open XML document conforms.
    
    ??? info "Example"

        Consider the following SpreadsheetML Workbook part markup:

        ```xml
        <workbook … conformance="transitional">
         …
        </workbook>
        ```

        This SpreadsheetML document has a conformance attribute value of transitional, therefore it conforms to the SML Transitional conformance class.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        **strict** (Office Open XML Strict) 

        :   Specifies that the document conforms to Office Open XML Strict.

        **transitional** (Office Open XML Transitional)

        :   Specifies that the document conforms to Office Open XML Transitional.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ConformanceClass) is located in §A.6.9. end note]

### 22.9.2.3 ST_FixedPercentage (带符号的固定百分比值)

=== "中文"

    此简单类型指定其内容将包含从 -100% 到 100%（包括 100%）的百分比测量值，包括尾随百分号 (U+0025)。

    ??? info "Example"

        考虑以下 WordprocessingML 片段：

        ```xml
        <w:tcPr>
         <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        属性的值是关联表格单元格的宽度。

    此简单类型的内容是 ST_Percentage 数据类型的限制 (§22.9.2.9).
    
    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `-?((100)|([0-9][0-9]?))(\.[0-9][0-9]?)?%`.

    [Note: 此简单类型的内容模型 (ST_FixedPercentage) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_FixedPercentage (Fixed Percentage Value with Sign)**

    This simple type specifies that its contents will contain a percentage measurement from -100% up to and including 100%, including a trailing percent sign (U+0025).

    ??? info "Example"

        Consider the following WordprocessingML fragment:

        ```xml
        <w:tcPr>
         <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        The value of the w attribute is the width of the associated table cell. 

    This simple type's contents are a restriction of the ST_Percentage datatype (§22.9.2.9).
    
    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `-?((100)|([0-9][0-9]?))(\.[0-9][0-9]?)?%`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_FixedPercentage) is located in §A.6.9. end note]

### 22.9.2.4 ST_Guid (128-Bit GUID)

=== "中文"

    此简单类型指定其值应为 128 位全局唯一标识符 (GUID) 值.

    ??? info "Example"

        考虑以下 WordprocessingML 片段，了解单个术语表文档条目的属性:

        ```xml
        <w:docPartPr>
         …
         <w:guid w:val="{00000000-5BD2-4BC8-9F70-7020E1357FB2}" />
         …
        </w:docPartPr>
        ```

        guid 元素指定与父条目关联的唯一标识符应为{00000000-5BD2-4BC8-9F70-7020E1357FB2}。 应用程序可以根据需要使用该值，例如，唯一地标识一个部件，无论其名称如何。

    此简单类型的内容是 W3C XML 架构令牌数据类型的限制。
    
    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `\{[0-9A-F]{8}-[0-9AF]{4}-[0-9A-F]{4}-[0-9A-F]{4}-[0-9A-F]{12}\}`.

    [Note: 此简单类型的内容模型 (ST_Guid) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_Guid (128-Bit GUID)**

    This simple type specifies that its values shall be a 128-bit globally unique identifier (GUID) value.

    ??? info "Example"

        Consider the following WordprocessingML fragment for the properties of a single glossary document entry

        ```xml
        <w:docPartPr>
         …
         <w:guid w:val="{00000000-5BD2-4BC8-9F70-7020E1357FB2}" />
         …
        </w:docPartPr>
        ```

        The guid element specifies that the unique identifier associated with the parent entry shall be {00000000- 5BD2-4BC8-9F70-7020E1357FB2}. This value can be used as needed by an application, for example, to uniquely identify a part regardless of its name

    This simple type's contents are a restriction of the W3C XML Schema token datatype.
    
    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `\{[0-9A-F]{8}-[0-9AF]{4}-[0-9A-F]{4}-[0-9A-F]{4}-[0-9A-F]{12}\}`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Guid) is located in §A.6.9. end note]

### 22.9.2.5 ST_HexColorRGB (十六进制颜色值)

=== "中文"

    此简单类型指定其内容应包含 RRGGBB 十六进制格式的颜色值，使用六个十六进制数字指定。 每个红色、绿色和蓝色颜色值（从 0 到 255）都编码为两个十六进制数字。

    ??? info "Example"

        考虑如下定义的颜色：

        ```text
        Red: 122
        Green: 23
        Blue: 209
        ```

        生成的 RRGGBB 值将是 7A17D1，因为每种颜色都会转换为其十六进制等效值。

    此简单类型的内容是 W3C XML Schema hexBinary 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 这个简单类型的内容的长度正好是 6 个十六进制数字。

    [Note: 此简单类型的内容模型 (ST_HexColorRGB) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_HexColorRGB (Hexadecimal Color Value)**

    This simple type specifies that its contents shall contain a color value in RRGGBB hexadecimal format, specified using six hexadecimal digits. Each of the red, green, and blue color values, from 0-255, is encoded as two hexadecimal digits.

    ??? info "Example"

        Consider a color defined as follows:

        ```text
        Red: 122
        Green: 23
        Blue: 209
        ```

        The resulting RRGGBB value would be 7A17D1, as each color is transformed into its hexadecimal equivalent.

    This simple type's contents are a restriction of the W3C XML Schema hexBinary datatype.
    
    This simple type also specifies the following restrictions:

    - This simple type's contents have a length of exactly 6 hexadecimal digit(s).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_HexColorRGB) is located in §A.6.9. end note]

### 22.9.2.6 ST_Lang (语言参考)

=== "中文"

    此简单类型指定其内容包含 RFC 4646/BCP 47 定义的语言标识符。

    该语言的内容是根据父 XML 元素的上下文进行解释的。

    ??? info "Example"

        考虑定义如下的语言代码：

        ```xml
        <w:lang w:val="en-CA" />
        ```

        因此，该语言被指定为英语 (en) 和加拿大 (CA)，从而使用英语（加拿大）语言设置.

    此简单类型的内容是 W3C XML Schema 字符串数据类型的限制

    [Note: 此简单类型的内容模型 (ST_Lang) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_Lang (Language Reference)**

    This simple type specifies that its contents contains a language identifier as defined by RFC 4646/BCP 47.

    The contents of this language are interpreted based on the context of the parent XML element.

    ??? info "Example"

        Consider a language code defined as follows :

        ```xml
        <w:lang w:val="en-CA" />
        ```

        This language is therefore specified as English (en) and Canada (CA), resulting in use of the English (Canada) language setting.

    This simple type's contents are a restriction of the W3C XML Schema string datatype

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Lang) is located in §A.6.9. end note]

### 22.9.2.7 ST_OnOff (开/关值)

=== "中文"

    此简单类型为 WordprocessingML 文档中定义的任何二进制（true 或 false）属性指定一组值。

    值 1 或 true 指定应打开该属性。 这是该属性的默认值，当父元素存在时隐含该值，但该属性被省略。

    值 0 或 false 指定应显式关闭该属性。

    此简单类型的内容是 W3C XML Schema 布尔数据类型的限制

    [Note: 此简单类型的内容模型 (ST_OnOff) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_OnOff (On/Off Value)**

    This simple type specifies a set of values for any binary (true or false) property defined in a WordprocessingML document.

    A value of 1 or true specifies that the property shall be turned on. This is the default value for this attribute, and is implied when the parent element is present, but this attribute is omitted. 

    A value of 0 or false specifies that the property shall be explicitly turned off.

    This simple type's contents are a restriction of the W3C XML Schema boolean datatype

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_OnOff) is located in §A.6.9. end note]

### 22.9.2.8 ST_Panose (Panose-1整数)

=== "中文"

    此简单类型指定 Panose-1 字体分类。 该值用作一条信息，以在所需字体不可用时指导选择类似的替代字体。

    [Guidance: ISO/IEC 14496-22 引用 1997 年的 Panose 规范，但 ECMA-376 的某些实现可能遵循 Panose 规范的较旧前体版本。 两个版本之间的某些值不兼容，这些差异的处理是实现定义的。

    为旧版本设计的 Panose-1 值应匹配以下 3 个正则表达式之一：

    - `\s*(00\s*){10}\s*`
    - `\s*(01\s*){10}\s*`
    - `\s*0[2-5]\s*0[0-9A-Fa-f]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9ABab]\s*0[0-9A-Fa-f]\s*0[0-9A-Da-d]\s*0[0-7]\s*`
    

    为 ISO/IEC 14496-22 设计的 Panose-1 值应与以下 6 个正则表达式之一匹配：

    - `\s*(00\s*){10}\s*`
    - `\s*(01\s*){10}\s*`
    - `\s*02\s*0[0-9A-Fa-f]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9ABab]\s*0[0-9A-Fa-f]\s*0[0-9A-Da-d]\s*0[0-7]\s*`
    - `\s*03\s*0[0-9]\s*0[0-9ABab]\s*0[0-3]\s*0[0-6]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9A-Dad]\s*0[0-9A-Da-d]\s*0[0-6]\s*`
    - `\s*04\s*0[0-9A-Ca-c]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9A-Da-d]\s*(0[0-9A-Faf]|10)\s*0[0-7]\s*0[0-8]\s*0[0-9A-Fa-f]\s*0[0-5]\s*`
    - `\s*05\s*0[0-9A-Ca-c]\s*01\s*0[0-3]\s*01\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*`

    end guidance]

    ??? info "Example"

        考虑为单一字体存储的以下信息：

        ```xml
        <w:font w:name="Times New Roman">
            <w:panose1 w:val="02020603050405020304" />
            …
        </w:font>
        ```

        panose1 元素通过其 val 属性值 02020603050405020304 指定其 Panose-1 编号。

    此简单类型的内容是 W3C XML Schema hexBinary 数据类型的限制。

    这个简单类型还指定了以下限制：

    - 这个简单类型的内容的长度正好是 20 个十六进制数字。

    [Note: 此简单类型的内容模型 (ST_Panose) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_Panose (Panose-1 Number)**

    This simple type specifies a Panose-1 font classification. This value is used as one piece of information to guide selection of a similar alternate font if the desired font is unavailable.

    [Guidance: ISO/IEC 14496-22 refers to the Panose specification dated 1997, but some implementations of ECMA-376 may follow an older precursor version of the Panose specification. Some values between the two versions are incompatible and the handling of these differences is implementation-defined.

    Panose-1 values designed for the older version should match one of the following 3 regular expressions:

    ```text
    \s*(00\s*){10}\s*
    \s*(01\s*){10}\s*
    \s*0[2-5]\s*0[0-9A-Fa-f]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9ABab]\s*0[0-9A-Fa-f]\s*0[0-9A-Da-d]\s*0[0-7]\s*
    ```

    Panose-1 values designed for ISO/IEC 14496-22 should match one of the following 6 regular expressions:

    ```text
    \s*(00\s*){10}\s*
    \s*(01\s*){10}\s*
    \s*02\s*0[0-9A-Fa-f]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9ABab]\s*0[0-9A-Fa-f]\s*0[0-9A-Da-d]\s*0[0-7]\s*
    \s*03\s*0[0-9]\s*0[0-9ABab]\s*0[0-3]\s*0[0-6]\s*0[0-9]\s*0[0-9Aa]\s*0[0-9A-Dad]\s*0[0-9A-Da-d]\s*0[0-6]\s*\s*04\s*0[0-9A-Ca-c]\s*0[0-9ABab]\s*0[0-9]\s*0[0-9A-Da-d]\s*(0[0-9A-Faf]|10)\s*0[0-7]\s*0[0-8]\s*0[0-9A-Fa-f]\s*0[0-5]\s*\s*05\s*0[0-9A-Ca-c]\s*01\s*0[0-3]\s*01\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*0[0-9]\s*
    ```

    end guidance]

    ??? info "Example"

        Consider the following information stored for a single font:

        ```xml
        <w:font w:name="Times New Roman">
            <w:panose1 w:val="02020603050405020304" />
            …
        </w:font>
        ```

        The panose1 element specifies its Panose-1 number via its val attribute value of 02020603050405020304.

    This simple type's contents are a restriction of the W3C XML Schema hexBinary datatype.

    This simple type also specifies the following restrictions:

    - This simple type's contents have a length of exactly 20 hexadecimal digit(s).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Panose) is located in §A.6.9. end note]

### 22.9.2.9 ST_Percentage (带符号的百分比值)

=== "中文"

    此简单类型指定其内容将包含百分比测量值，并带有尾随百分号 (U+0025)。
    
    ??? info "Example"

        考虑以下 WordprocessingML 片段：
    
        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        w 属性的值是关联表格单元格的宽度。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `-?[0-9]+(\.[0-9]+)?%`.

    [Note: 此简单类型的内容模型 (ST_Percentage) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_Percentage (Percentage Value with Sign)**

    This simple type specifies that its contents will contain a percentage measurement, with a trailing percent sign (U+0025).
    
    ??? info "Example"

        Consider the following WordprocessingML fragment:
    
        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        The value of the w attribute is the width of the associated table cell.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `-?[0-9]+(\.[0-9]+)?%`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Percentage) is located in §A.6.9. end note]

### 22.9.2.10 ST_PositiveFixedPercentage (带符号的正固定百分比值)

=== "中文"

    此简单类型指定其内容将包含从 0% 到 100%（含）的正百分比测量值，包括尾随百分号 (U+0025)。

    ??? info "Example"

        考虑以下 WordprocessingML 片段：

        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        w 属性的值是关联表格单元格的宽度。

    此简单类型的内容是 ST_Percentage 数据类型的限制 (§22.9.2.9)

    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `((100)|([0-9][0-9]?))(\.[0-9][0-9]?)?%`.

    [Note: 此简单类型的内容模型 (ST_PositiveFixedPercentage) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_PositiveFixedPercentage (Positive Fixed Percentage Value with Sign)**

    This simple type specifies that its contents will contain a positive percentage measurement from 0% to 100% inclusive, including a trailing percent sign (U+0025).

    ??? info "Example"

        Consider the following WordprocessingML fragment:

        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        The value of the w attribute is the width of the associated table cell. 

    This simple type's contents are a restriction of the ST_Percentage datatype (§22.9.2.9)

    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `((100)|([0-9][0-9]?))(\.[0-9][0-9]?)?%`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveFixedPercentage) is located in §A.6.9. end note]

### 22.9.2.11 ST_PositivePercentage (带符号的正百分比值)

=== "中文"

    此简单类型指定其内容将包含正百分比测量值，包括尾随百分号 (U+0025)。
    
    ??? info "Example"

        考虑以下 WordprocessingML 片段：

        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        w 属性的值是关联表格单元格的宽度。

    此简单类型的内容是 ST_Percentage 数据类型的限制 (§22.9.2.9).

    这个简单类型还指定了以下限制：

    - 此简单类型的内容应与以下正则表达式模式匹配： `[0-9]+(\.[0-9]+)?%`.

    [Note: 此简单类型的内容模型 (ST_PositivePercentage) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_PositivePercentage (Positive Percentage Value with Sign)**

    This simple type specifies that its contents will contain a positive percentage measurement, including a trailing percent sign (U+0025).
    
    ??? info "Example"

        Consider the following WordprocessingML fragment:

        ```xml
        <w:tcPr>
            <w:tcW w:type="pct" w:w="33.3%" />
        </w:pPr>
        ```

        The value of the w attribute is the width of the associated table cell. 

    This simple type's contents are a restriction of the ST_Percentage datatype (§22.9.2.9).

    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `[0-9]+(\.[0-9]+)?%`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositivePercentage) is located in §A.6.9. end note]

### 22.9.2.12 ST_PositiveUniversalMeasure (积极的普遍测量)

=== "中文"

    这种简单类型指定其内容将包含使用常用度量单位之一表示的度量。 该类型的内容是一个正十进制数，后面紧跟一个单位标识符。 单位标识符区分大小写，并且应为小写。 符合要求的应用程序不需要在加载和保存特定文档之间保留度量单位。
    
    应支持与 ST_UniversalMeasure 类型 (§22.9.2.15) 中相同的测量单位集。
    
    此简单类型的内容是 ST_UniversalMeasure 数据类型的限制 (§22.9.2.15).
    
    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `[0-9]+(\.[0-9]+)?(mm|cm|in|pt|pc|pi)`.

    [Note: 此简单类型的内容模型 (ST_PositiveUniversalMeasure) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_PositiveUniversalMeasure (Positive Universal Measurement)**

    This simple type specifies that its contents will contain a measurement expressed using one of common measure units. The content of this type is a positive decimal number immediately followed by a unit identifier. Unit identifiers are case sensitive and shall be in lowercase. Conforming applications are not required to preserve units of measure between loading and saving a particular document.
    
    The same set of units of measure as in ST_UniversalMeasure type (§22.9.2.15) shall be supported.
    
    This simple type's contents are a restriction of the ST_UniversalMeasure datatype (§22.9.2.15).
    
    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `[0-9]+(\.[0-9]+)?(mm|cm|in|pt|pc|pi)`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_PositiveUniversalMeasure) is located in §A.6.9. end note]

### 22.9.2.13 ST_String (字符串)

=== "中文"

    这个简单类型指定其内容包含一个字符串。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    [Note: 此简单类型的内容模型 (ST_String) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **String**

    This simple type specifies that its contents contains a string.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_String) is located in §A.6.9. end note]

### 22.9.2.14 ST_TwipsMeasure (以二十分之一点为单位的测量)

=== "中文"

    这个简单类型指定其内容包含凋灵：

    - 正整数，其内容由二十分之一点的测量值（相当于 1/1440 英寸）组成，或者
    - 紧跟单位标识符的正十进制数。
    
    此测量的内容是根据父 XML 元素的上下文进行解释的。

    [Example: 考虑类型为 ST_TwipsMeasure 的属性值 720。 此属性值指定二分之一英寸或 36 点（720 二十分之一点 = 36 点 = 0.5 英寸）的大小。 end example]
    
    [Example: 考虑类型为 ST_HpsMeasure 的属性值 12.7mm。 该属性值指定尺寸为 0.0127 米或二分之一英寸或 36 点。 end example]
    
    这个简单类型是以下类型的联合：

    - ST_PositiveUniversalMeasure 简单类型 (§22.9.2.12).
    - ST_UnsignedDecimalNumber 简单类型 (§22.9.2.16).

    [Note: 此简单类型的内容模型 (ST_TwipsMeasure) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_TwipsMeasure (Measurement in Twentieths of a Point)**

    This simple type specifies that its contents contain wither:

    - A positive whole number, whose contents consist of a measurement in twentieths of a point (equivalent to 1/1440th of an inch), or
    - A positive decimal number immediately following by a unit identifier.
    
    The contents of this measurement are interpreted based on the context of the parent XML element.

    [Example: Consider an attribute value of 720 whose type is ST_TwipsMeasure. This attribute value specifies a size of one-half of an inch or 36 points (720 twentieths of a point = 36 points = 0.5 inches). end example]
    
    [Example: Consider an attribute value of 12.7mm whose type is ST_HpsMeasure. This attribute value specifies a size of 0.0127 meter or one-half of an inch or 36 points. end example]
    
    This simple type is a union of the following types:

    - The ST_PositiveUniversalMeasure simple type (§22.9.2.12).
    - The ST_UnsignedDecimalNumber simple type (§22.9.2.16).

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_TwipsMeasure) is located in §A.6.9. end note]

### 22.9.2.15 ST_UniversalMeasure (通用测量)

=== "中文"

    这种简单类型指定其内容将包含使用常用度量单位之一表示的度量。 该类型的内容是一个十进制数，后面紧跟一个单位标识符。 单位标识符区分大小写，并且应为小写。 符合要求的应用程序不需要在加载和保存特定文档之间保留度量单位。
    
    下表列出了允许的计量单位及其基于现有标准的定义或表示为其他计量单位的换算。

    | 单位标识符 | 定义 |
    |---|---|
    |cm | 按照 ISO 31 的定义。 | 
    |mm | 按照 ISO 31 的定义。 | 
    |in | 1 in = 2.54 cm (informative) | 
    |pt | 1 pt = 1/72 in (informative) | 
    |pc | 1 pc = 12 pt (informative) | 
    |pi | 1 pi = 12 pt (informative) | 
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    这个简单类型还指定了以下限制：

    - 该简单类型的内容应与以下正则表达式模式匹配: `-?[0-9]+(\.[0-9]+)?(mm|cm|in|pt|pc|pi)`.

    [Note: 此简单类型的内容模型 (ST_UniversalMeasure) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_UniversalMeasure (Universal Measurement)**

    This simple type specifies that its contents will contain measurement expressed using one of common measure units. The content of this type is a decimal number immediately followed by a unit identifier. Unit identifiers are case sensitive and shall be in lowercase. Conforming applications are not required to preserve units of measure between loading and saving a particular document.
    
    The following table lists units of measure which are allowed together with their definition based on existing standard or expressed as a conversion from other unit of measure.

    | Unit Identifier | Definition |
    |---|---|
    |cm | As defined in ISO 31. | 
    |mm | As defined in ISO 31. | 
    |in | 1 in = 2.54 cm (informative) | 
    |pt | 1 pt = 1/72 in (informative) | 
    |pc | 1 pc = 12 pt (informative) | 
    |pi | 1 pi = 12 pt (informative) | 
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type also specifies the following restrictions:

    - This simple type's contents shall match the following regular expression pattern: `-?[0-9]+(\.[0-9]+)?(mm|cm|in|pt|pc|pi)`.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_UniversalMeasure) is located in §A.6.9. end note]

### 22.9.2.16 ST_UnsignedDecimalNumber (无符号十进制数值)

=== "中文"

    此简单类型指定其内容包含正整数十进制数，其内容根据父 XML 元素的上下文进行解释。

    ??? info "Example"

        考虑以下 WordprocessingML 片段：

        ```xml
        <w:pPr>
            <w:divId w:val="1512645511" />
        </w:pPr>
        ```
        
        val 属性的值是关联的 HTML div 的 ID。

        但是，请考虑以下片段：

        ```xml
        <w:ilvl w:val="1">
         …
        </w:ilvl>
        ```

        在这种情况下，val属性中的十进制数字是关联编号级别的ID。 在每种情况下，十进制数值都在父元素的上下文中进行解释。

    此简单类型的内容是 W3C XML Schema unsignedLong 数据类型的限制。
    
    [Note: 此简单类型的内容模型 (ST_UnsignedDecimalNumber) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_UnsignedDecimalNumber(Unsigned Decimal Number Value)**

    This simple type specifies that its contents contain a positive whole decimal number, whose contents are interpreted based on the context of the parent XML element.

    ??? info "Example"

        Consider the following WordprocessingML fragment:

        ```xml
        <w:pPr>
            <w:divId w:val="1512645511" />
        </w:pPr>
        ```
        
        The value of the val attribute is the ID of the associated HTML div.

        However, consider the following fragment:

        ```xml
        <w:ilvl w:val="1">
         …
        </w:ilvl>
        ```

        In this case, the decimal number in the val attribute is the ID of the associated numbering level. In each case, the decimal number value is interpreted in the context of the parent element.

        This simple type's contents are a restriction of the W3C XML Schema unsignedLong datatype.

        [Note: The W3C XML Schema definition of this simple type’s content model (ST_UnsignedDecimalNumber) is located in §A.6.9. end note]

### 22.9.2.17 ST_VerticalAlignRun (垂直定位位置)

=== "中文"

    此简单类型指定此运行内容相对于运行文本的默认外观的对齐方式的可能值。 这允许将文本重新定位为下标或上标，而无需更改运行属性的字体大小.
    
    ??? info "Example"

        考虑一个在显示其内容时必须定位为上标的运行。 此要求将使用以下 WordprocessingML 指定：

        ```xml
        <w:rPr>
            <w:vertAlign w:val="superscript" />
        </w:rPr>
        ```

        生成的运行定位为上标，因此它以运行内容的默认基线位置上方的较小尺寸呈现。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：

    ??? abstract "枚举"

        **baseline** (常规垂直定位/Regular Vertical Positioning)

        :   指定父运行中的文本应位于基线处并以与周围文本相同的大小显示.
        
        **subscript** (下标/Subscript)

        :   指定该文本应该是下标。

            此设置应将此运行中的文本降低到基线以下，并将其更改为较小的尺寸（如果有较小的尺寸可用）。

        **superscript** (上标/Superscript)

        :   指定该文本应为上标。

            此设置应将本次运行中的文本升高到基线以上，并将其更改为较小的尺寸（如果有较小的尺寸可用）。
    
    [Note: 此简单类型的内容模型 (ST_VerticalAlignRun) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **ST_VerticalAlignRun(Vertical Positioning Location)**

    This simple type specifies possible values for the alignment of the contents of this run in relation to the default appearance of the run's text. This allows the text to be repositioned as subscript or superscript without altering the font size of the run properties.
    
    ??? info "Example"

        Consider a run which must be positioning as superscript when displaying its contents. This requirement would be specified using the following WordprocessingML:

        ```xml
        <w:rPr>
            <w:vertAlign w:val="superscript" />
        </w:rPr>
        ```

        The resulting run is positioned as superscript, therefore it is rendered in a smaller size above the default baseline location for the contents of the run.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        baseline (Regular Vertical Positioning)

        :   Specifies that the text in the parent run shall be located at the baseline and presented in the same size as surrounding text.
        
        subscript (Subscript)

        :   Specifies that this text should be subscript.

            This setting shall lower the text in this run below the baseline and change it to a smaller size, if a smaller size is available.

        superscript (Superscript)

        :   Specifies that this text should be superscript.

            This setting shall raise the text in this run above the baseline and change it to a smaller size, if a smaller size is available.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_VerticalAlignRun) is located in §A.6.9. end note]

### 22.9.2.18 ST_XAlign (水平对齐位置)

=== "中文"

    这个简单类型指定父浮动对象的一组可能的相对水平位置。 该相对位置是相对于父对象指定的水平锚点指定的。

    ??? info "Example"

        考虑以下指定文本框架的 WordprocessingML 片段：

        ```xml
        <w:p>
            <w:pPr>
                <w:framePr w:w="2419" w:h="2189" w:hRule="atLeast" w:hSpace="187"
                w:wrap="around" w:vAnchor="text" w:hAnchor="page" w:xAlign="left" w:y="73" />
            </w:pPr>
            <w:r>
                <w:t>Text Frame Content.</w:t>
            </w:r>
        </w:p>
        ```

        此文本框架通过 xAlign 属性的存在指定将框架与锚点对象（在本例中为页面）的左侧对齐。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：

    ??? abstract "Enumeration"

        **center** (水平居中/Centered Horizontally)

        :   指定父对象应相对于锚点设置居中。

            [Example: 页面水平居中. end example]

        **inside** (里面/Inside) 

        :   指定父对象应位于锚点对象内部。

            [Example: 水平文本边距内. end example]

        **left** (水平左对齐/Left Aligned Horizontally)

        :   指定父对象应相对于锚点设置左对齐。

            [Example: 在页面上水平左对齐.  end example]

        **outside** (外部/Outside)

        :   指定父对象应位于锚点对象之外.

            [Example: 水平文本边距之外. end example]

        **right** (水平右对齐/Right Aligned Horizontally)

        :   指定父对象应相对于锚点设置右对齐.

            [Example: 在页面上水平右对齐. end example]

    [Note: 此简单类型的内容模型 (ST_XAlign) 的 W3C XML 架构定义位于 §A.6.9. end note]

=== "英文"

    **(Horizontal Alignment Location)**

    This simple type specifies the set of possible relative horizontal positions for the parent floating object. This relative position is specified relative to the horizontal anchor specified by the parent object.

    ??? info "Example"

        Consider the following WordprocessingML fragment specifying a text frame:

        ```xml
        <w:p>
            <w:pPr>
                <w:framePr w:w="2419" w:h="2189" w:hRule="atLeast" w:hSpace="187"
                w:wrap="around" w:vAnchor="text" w:hAnchor="page" w:xAlign="left" w:y="73" />
            </w:pPr>
            <w:r>
                <w:t>Text Frame Content.</w:t>
            </w:r>
        </w:p>
        ```

        This text frame specifies by the presence of the xAlign attribute to align the frame on the left side of the anchor object, in this case, the page. 

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        center (Centered Horizontally)

        :   Specifies that the parent object shall be centered with respect to the anchor settings.

            [Example: Centered on the page horizontally. end example]

        inside (Inside) 

        :   Specifies that the parent object shall be inside of the anchor object.

            [Example: Inside the text margin horizontally. end example]

        left (Left Aligned Horizontally)

        :   Specifies that the parent object shall be left aligned with respect to the anchor settings.

            [Example: Left aligned on the page horizontally.  end example]

        outside (Outside)

        :   Specifies that the parent object shall be outside of the anchor object.

            [Example: Outside the text margin horizontally. end example]

        right (Right Aligned Horizontally)

        :   Specifies that the parent object shall be right aligned with respect to the anchor settings.

            [Example: Right aligned on the page horizontally. end example]

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_XAlign) is located in §A.6.9. end note]

### 22.9.2.19 ST_Xstring (转义字符串)

=== "中文"

    支持转义无效 XML 字符的字符串。

    对于 XML 1.0 规范定义的无法在 XML 中表示的所有字符，将使用 Unicode 数字字符表示转义字符格式 `_xHHHH_` 对这些字符进行转义，其中 H 表示字符值中的十六进制字符. [Example: XML 1.0 文档中不允许使用 Unicode 字符 8，因此必须将其转义为 `_x0008_`。 end example]
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。
    
    [Note: 此简单类型的内容模型 (ST_Xstring) 的 W3C XML 架构定义位于 §A.6.9. end note]

=== "英文"

    **(Escaped String)**

    String of characters with support for escaped invalid-XML characters.

    For all characters which cannot be represented in XML as defined by the XML 1.0 specification, the characters are escaped using the Unicode numerical character representation escape character format _xHHHH_, where H represents a hexadecimal character in the character's value. [Example: The Unicode character 8 is not permitted in an XML 1.0 document, so it must be escaped as _x0008_. end example]
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Xstring) is located in §A.6.9. end note]

### 22.9.2.20 ST_YAlign (垂直对齐位置)

=== "中文"

    这个简单类型指定父浮动对象的一组可能的相对垂直位置。 该相对位置是相对于父对象指定的垂直锚点指定的。

    ??? info "Example"

        考虑以下指定文本框架的 WordprocessingML 片段：

        ```xml
        <w:p>
            <w:pPr>
                <w:framePr w:w="2419" w:h="2189" w:hRule="atLeast" w:hSpace="187"
                w:wrap="around" w:vAnchor="margin" w:hAnchor="page" w:x="1643" w:y="73"
                w:yAlign="center" />
            </w:pPr>
            <w:r>
                <w:t>Text Frame Content.</w:t>
            </w:r>
        </w:p>
        ```

        此文本框架通过 yAlign 属性的存在指定将框架垂直对齐于锚点对象的中心（在本例中为边距）。 
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：

    ??? abstract "枚举值"

        **bottom** (底部/Bottom)

        :   指定父对象应与锚点对象的下边缘垂直对齐。

            [Example: 在当前段落的底部. end example]

        **center** (垂直居中/Centered Vertically)

        :   指定父对象应相对于锚点对象垂直居中。 不得与 baseJc 元素一起使用。

            [Example: 页面垂直居中. end example]

        **inline** (与文字一致/In line With Text)

        :   指定父对象应与周围文本垂直对齐 (i.e. 当放置在文档中时，不得允许任何文本环绕它。 不得与基本元件一起使用.)

        **inside** (内部锚点范围 / Inside Anchor Extents)

        :   指定父对象应与锚点对象的边缘垂直对齐，并位于该对象内部。 不得与 baseJc 元素一起使用。

            [Example: 文本边距内部垂直. end example]

        **outside** (外锚范围 / Outside Anchor Extents) 

        :   指定父对象应与锚点对象的边缘垂直对齐，并位于该对象的外部。 不得与 base 元素一起使用。

            [Example: 垂直方向位于文本边距之外.  end example]

        **top** (顶部 / Top) 

        :   指定父对象应与锚点对象的上边缘垂直对齐 .

            [Example: 在当前段落的顶部. end example]
    
    [Note: 此简单类型的内容模型 (ST_YAlign) 的 W3C XML 架构定义位于 §A.6.9 中。 end note]

=== "英文"

    **(Vertical Alignment Location)**

    This simple type specifies the set of possible relative vertical positions for the parent floating object. This relative position is specified relative to the vertical anchor specified by the parent object.

    ??? info "Example"

        Consider the following WordprocessingML fragment specifying a text frame:

        ```xml
        <w:p>
            <w:pPr>
                <w:framePr w:w="2419" w:h="2189" w:hRule="atLeast" w:hSpace="187"
                w:wrap="around" w:vAnchor="margin" w:hAnchor="page" w:x="1643" w:y="73"
                w:yAlign="center" />
            </w:pPr>
            <w:r>
                <w:t>Text Frame Content.</w:t>
            </w:r>
        </w:p>
        ```

        This text frame specifies by the presence of the yAlign attribute to vertically align the frame in the center of the anchor object, in this case, the margin. 
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    This simple type is restricted to the values listed in the following table:

    ??? abstract "Enumeration"

        bottom (Bottom)

        :   Specifies that the parent object shall be vertically aligned to the bottom edge of the anchor object.

            [Example: At the bottom of the current paragraph. end example]

        center (Centered Vertically)

        :   Specifies that the parent object shall be vertically centered with respect to the anchor object. Shall not be used with the baseJc element. 

            [Example: Centered on the page vertically. end example]

        inline (In line With Text)

        :   Specifies that the parent object shall be vertically aligned in line with the surrounding text (i.e. shall not allow any text wrapping around it when positioned in the document. Shall not be used with the base element.)

        inside (Inside Anchor Extents)

        :   Specifies that the parent object shall be vertically aligned to the edge of the anchor object, and positioned inside that object. Shall not be used with the baseJc element.

            [Example: Inside the text margins vertically. end example]

        outside (Outside Anchor Extents) 

        :   Specifies that the parent object shall be vertically aligned to the edge of the anchor object, and positioned outside that object. Shall not be used with the baseJc element.

            [Example: Outside the text margins vertically.  end example]

        top (Top) 

        :   Specifies that the parent object shall be vertically aligned to the top edge of the anchor object .

            [Example: At the top of the current paragraph. end example]
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_YAlign) is located in §A.6.9. end note]

### 22.9.2.21 ST_XmlName (XML 名称)

=== "中文"

    此简单类型应包含 XML 非殖民名称 (NCName)。

    ??? info "Example"

        请考虑以下 WordprocessingML 片段，了解单个自定义 XML 元素的属性:

        ```xml
        <w:customXmlPr>
        <w:attr w:name="company" w:uri="http://schemas.openxmlformats.org/2006/example"
        … />
        </w:customXmlPr>
        ```

        attr 元素指定与属性名称关联的 NCName 应为 company. 

    此简单类型的内容是 W3C XML Schema NCName 数据类型的限制。

=== "英文"

    **ST_XmlName(XML Name)**

    This simple type shall contain an XML non-colonized name (NCName).

    ??? info "Example"

        Consider the following WordprocessingML fragment for the properties of a single custom XML element:

        ```xml
        <w:customXmlPr>
        <w:attr w:name="company" w:uri="http://schemas.openxmlformats.org/2006/example"
        … />
        </w:customXmlPr>
        ```

        The attr element specifies that the NCName associated with the attribute name shall be company. 

    This simple type's contents are a restriction of the W3C XML Schema NCName datatype.
