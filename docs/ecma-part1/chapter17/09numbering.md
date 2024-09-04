# 17.9 编号

**Numbering**

=== "中文"
    
    编号指的是符号 - 阿拉伯数字、罗马数字、符号字符（"项目符号"）、文本串等 - 在WordprocessingML中用于标记单独段落的标签。
    
    【示例：以下两个段落分别包含WordprocessingML中定义的编号：第一个使用阿拉伯数字，第二个使用符号字符：
    
    7.&nbsp;这是一个带有编号信息的段落。
    
    - 这也是一个带有编号信息的段落。
    
    示例结束】
    
    WordprocessingML中所有编号的基础通过两种结构指定：
    
    - 抽象编号定义
    - 编号定义实例
    
    抽象编号定义定义文档中一组指定段落的外观和行为。由于此结构是抽象的，因此不会被文档内容直接引用，而是应被编号定义实例继承，后者本身被文档内容引用。
    
    【示例：考虑WordprocessingML文档中抽象编号定义的以下示例：

    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            <w:start w:val="1" />
            <w:lvlText w:val="%1." />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    ```
    
    此abstractNum元素定义了一组编号属性的抽象编号定义。它被继承自一个抽象NumId等于4的任何编号定义实例：

    ```xml
    <w:num w:numId="2">
        <w:abstractNumId w:val="4" />
    </w:num>
    ```
    
    此num元素定义了一个编号定义实例，可以定义对抽象编号定义的覆盖（在此情况下没有），并且被任何带有numId等于2的段落使用：

    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="2" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>一级标题</w:t>
        </w:r>
    </w:p>
    ```
    
    结果段落继承了编号定义实例2的级别0属性，它就是编号定义4的抽象编号定义的一个实例。示例结束】

=== "英文"
    
    Numbering refers to symbols - Arabic numerals, Roman numerals, symbol characters ("bullets"), text strings, etc. - in WordprocessingML that are used to label individual paragraphs of text.
    
    [Example: The following two paragraphs each contain numbering as defined by WordprocessingML: the first uses an Arabic numeral, the second a symbol character:
    
    7.&nbsp;This is a paragraph with numbering information.
    
    - This is also a paragraph with numbering information.
    
    end example]
    
    The basis for all numbering in WordprocessingML is specified via two structures:
    
    - abstract numbering definitions
    - numbering definition instances
    
    Abstract numbering definitions define the appearance and behavior of a specific set of numbered paragraphs in a document. Because this construct is abstract, they are not be directly referenced by document content, but rather they shall be inherited by a numbering definition instance, which itself is referenced by document content.
    
    [Example: Consider the following example of an abstract numbering definition in a WordprocessingML
    document:
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            <w:start w:val="1" />
            <w:lvlText w:val="%1." />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    ```
    
    This abstractNum element defines an abstract numbering definition which defines a set of numbering properties. It is inherited by any numbering definition instance which inherits from an abstractNumId equal to 4:
    
    ```xml
    <w:num w:numId="2">
        <w:abstractNumId w:val="4" />
    </w:num>
    ```
    
    This num element defines an numbering definition instance which can define overrides to the abstract numbering definition (in this case it does not), and is used by any paragraphs with a numId equal to 2:
    
    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="2" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Level one</w:t>
        </w:r>
    </w:p>
    ```
    
    The resulting paragraph inherits the properties of level 0 in the numbering definition instance of 2 which is simply a instance of the abstract numbering definition of 4. end example]

## 17.9.1 abstractNum (摘要编号定义)

**abstractNum (Abstract Numbering Definition)**

=== "中文"
    
    此元素指定了一组属性，这些属性将决定 WordprocessingML 文档中一组编号段落的外观和行为。这些属性统称为抽象编号定义，是所有编号信息在 WordprocessingML 文档中的基础。
    
    虽然抽象编号定义包含了一整套编号信息，但它不会被内容直接引用（因此称为抽象）。相反，这些属性将通过编号定义实例使用 num 元素 ([§17.9.15]) 继承，然后该实例本身可以被内容引用。
    
    【示例：请考虑以下 WordprocessingML 文档中 abstractNum 的示例：
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            <w:start w:val="1" />
            <w:lvlText w:val="%1." />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    ```
    
    此 abstractNum 元素定义了一个抽象编号定义，任何从抽象编号定义继承且 abstractNumId 等于 4 的编号定义实例必须继承它。示例结束】
    
    ??? abstract "Attributes"
    
        **abstractNumId**（抽象编号定义ID）
        
        :   指定一个唯一的编号，作为此抽象编号定义的标识符。任何编号定义实例要继承此抽象编号定义指定的属性，必须引用此唯一编号。
        
            【示例：请考虑一个 abstractNumId 属性为 4 的抽象编号定义的 WordprocessingML 代码：
            
            ```xml
            <w:abstractNum w:abstractNumId="4">
                <w:nsid w:val="FFFFFF7F" />
                <w:multiLevelType w:val="singleLevel" />
                <w:lvl w:ilvl="0">
                    <w:start w:val="1" />
                    <w:lvlText w:val="%1." />
                    <w:lvlJc w:val="start" />
                    <w:pPr>
                        <w:tabs>
                            <w:tab w:val="num" w:pos="720" />
                        </w:tabs>
                        <w:ind w:left="720"/>
                    </w:pPr>
                </w:lvl>
            </w:abstractNum>
            ```
            
            abstractNumId 属性作为抽象编号定义的唯一标识符，使具有匹配属性值的 abstractNumId 元素的编号定义实例 ([§17.9.15]) 能够继承抽象编号定义的属性，例如：
            
            ```xml
            <w:numbering>
                …
                <w:num w:numId="2">
                    <w:abstractNumId w:val="0" />
                </w:num>
                <w:num w:numId="3">
                    <w:abstractNumId w:val="1" />
                </w:num>
                <w:num w:numId="4">
                    <w:abstractNumId w:val="4" />
                </w:num>
                <w:num w:numId="5">
                    <w:abstractNumId w:val="4" />
                </w:num>
            </w:numbering>
            ```
            
            在这种情况下，最后两个编号定义实例都继承自 abstractNumId 为 4 的抽象编号定义。示例结束】
            
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AbstractNum) is located in §A.1. end note]

=== "英文"
    
    This element specifies a set of properties which shall dictate the appearance and behavior of a set of numbered paragraphs in a WordprocessingML document. These properties are collectively called an abstract numbering definition, and are the basis for all numbering information in a WordprocessingML document.
    
    Although an abstract numbering definition contains a complete set of numbering, it shall not be directly referenced by content (hence the use of abstract). Instead, these properties shall be inherited by a numbering definition instance using the num element ([§17.9.15]), which can then itself be referenced by content.
    
    [Example: Consider the following example of an abstractNum in a WordprocessingML document:
    
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            <w:start w:val="1" />
            <w:lvlText w:val="%1." />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    
    
    This abstractNum element defines an abstract numbering definition which must be inherited by any numbering definition instance which inherits from abstract numbering definition with an abstractNumId equal to 4. end example]
    
    
    ??? abstract "Attributes"
    
        **abstractNumId** (Abstract Numbering Definition ID)
    
        :   Specifies a unique number which shall be used as the identifier for this abstract numbering definition. This unique number shall be referenced by any numbering definition instance in order to inherit the properties specified by this abstract numbering definition.
            
            [Example: Consider the WordprocessingML for an abstract numbering definition with an abstractNumId attribute of 4:
            
            ```xml
            <w:abstractNum w:abstractNumId="4">
                <w:nsid w:val="FFFFFF7F" />
                <w:multiLevelType w:val="singleLevel" />
                <w:lvl w:ilvl="0">
                    <w:start w:val="1" />
                    <w:lvlText w:val="%1." />
                    <w:lvlJc w:val="start" />
                    <w:pPr>
                        <w:tabs>
                            <w:tab w:val="num" w:pos="720" />
                        </w:tabs>
                        <w:ind w:left="720"/>
                    </w:pPr>
                </w:lvl>
            </w:abstractNum>
            ```
            
            The abstractNumId attribute serves as a unique identifier for the abstract numbering definition, allowing numbering definition instances ([§17.9.15]) with a abstractNumId element with a matching attribute value to inherit the abstract numbering definition properties, for example:
            
            
            ```xml
            <w:numbering>
                …
                <w:num w:numId="2">
                    <w:abstractNumId w:val="0" />
                </w:num>
                <w:num w:numId="3">
                    <w:abstractNumId w:val="1" />
                </w:num>
                <w:num w:numId="4">
                    <w:abstractNumId w:val="4" />
                </w:num>
                <w:num w:numId="5">
                    <w:abstractNumId w:val="4" />
                </w:num>
            </w:numbering>
            ```
            
            In this case, the final two numbering definition instances both inherit from the abstract numbering definition with a abstractNumId of 4. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AbstractNum) is located in §A.1. end note]



## 17.9.2 abstractNumId (摘要编号定义参考)

**abstractNumId (Abstract Numbering Definition Reference)**

=== "中文"

    此元素指定抽象编号定义信息，其属性将由父编号定义实例继承。
    
    【示例：请考虑一个包含两个编号定义实例的文档的 WordprocessingML，其中每个实例引用不同的抽象编号定义：
    
    ```xml
    <w:numbering>
        <w:abstractNum w:abstractNumId="0">
            …
        </w:abstractNum>
        <w:abstractNum w:abstractNumId="1">
            …
        </w:abstractNum>
        …
        <w:num w:numId="1">
            <w:abstractNumId w:val="0" />
        </w:num>
        <w:num w:numId="2">
            <w:abstractNumId w:val="1" />
        </w:num>
        …
    </w:numbering>
    ```
    
    这两个编号定义实例通过其 abstractNumId 元素分别引用 abstractNumId 属性值为 0 和 1 的抽象编号定义。示例结束】
    
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
        
        :   指定此属性的内容包含一个十进制数。
        
            该十进制数的内容根据父 XML 元素的上下文进行解释。
            
            【示例：请考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须在父元素的上下文中解释。示例结束】
            
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"

    This element specifies the abstract numbering definition information whose properties shall be inherited by the parent numbering definition instance.
    
    [Example: Consider the WordprocessingML for a document with two numbering definition instances, each referencing a different abstract numbering definition:
    
    ```xml
    <w:numbering>
        <w:abstractNum w:abstractNumId="0">
            …
        </w:abstractNum>
        <w:abstractNum w:abstractNumId="1">
            …
        </w:abstractNum>
        …
        <w:num w:numId="1">
            <w:abstractNumId w:val="0" />
        </w:num>
        <w:num w:numId="2">
            <w:abstractNumId w:val="1" />
        </w:num>
        …
    </w:numbering>
    ```
    
    The two numbering definition instances reference the abstract numbering definitions with abstractNumId attribute values of 0 and 1 respectively, via their abstractNumId elements. end example]
    
    
    ??? abstract "Attributes"
    
        val (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]
    
## 17.9.3 ilvl (编号级别参考)

**ilvl (Numbering Level Reference)**

=== "中文"
    
    此元素指定将应用于父段落的编号定义实例的编号级别。
    
    这个编号级别在抽象编号定义的 lvl 元素（[§17.9.6]）上指定，可以被编号定义实例级别覆盖的 lvl 元素（[§17.9.5]）重写。
    
    【示例：请考虑 WordprocessingML 文档中的以下编号段落：
    
    1. 级别一
    
        a. 级别二
    
    这些编号段落可能使用以下 WordprocessingML 表示：
    
    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
            <w:ilvl w:val="0" />
            <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>级别一</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
            <w:ilvl w:val="1" />
            <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>级别二</w:t>
        </w:r>
    </w:p>
    ```
    
    上述 WordprocessingML 指定第一个编号段落引用编号定义中 num 元素（[§17.9.15]）内编号级别为 0，numId 属性等于 5。
    
    第二个编号段落引用相同编号定义实例中编号级别为 1。上述 ilvl 元素引用的 WordprocessingML 如下：
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="0" />
    </w:num>
    …
    <w:abstractNum w:abstractNumId="0">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            …
        </w:lvl>
        <w:lvl w:ilvl="1">
            …
        </w:lvl>
    </w:abstractNum>
    ```
    
    在这种情况下，最终段落将分别继承 ilvl 属性为 0 和 1 的抽象编号定义级别的属性。示例结束】
    
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
        
        :   指定此属性的内容包含一个十进制数。
        
            该十进制数的内容根据父 XML 元素的上下文进行解释。
            
            【示例：请考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须在父元素的上下文中解释。示例结束】
            
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the numbering level of the numbering definition instance which shall be applied to the
    parent paragraph.
    
    This numbering level is specified on either the abstract numbering definition's lvl element ([§17.9.6]), and can be
    overridden by a numbering definition instance level override's lvl element ([§17.9.5]).
    
    [Example: Consider the following numbered paragraphs in a WordprocessingML document:
    
    1. Level one
    
        a. Level two
    
    These numbered paragraphs might be represented using the following WordprocessingML:
    
    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
            <w:ilvl w:val="0" />
            <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Level one</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
            <w:ilvl w:val="1" />
            <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Level two</w:t>
        </w:r>
    </w:p>
    ```
    
    The WordprocessingML above specifies that the first numbered paragraph references the numbering level of 0, within the numbering definition of the num element ([§17.9.15]) with a numId attribute equal to 5.
    
    The second numbered paragraph references the numbering of 1, within the same numbering definition instance. The WordprocessingML referenced by the ilvl elements above is given below:
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="0" />
    </w:num>
    …
    <w:abstractNum w:abstractNumId="0">
        <w:nsid w:val="FFFFFF7F" />
        <w:multiLevelType w:val="singleLevel" />
        <w:lvl w:ilvl="0">
            …
        </w:lvl>
        <w:lvl w:ilvl="1">
            …
        </w:lvl>
    </w:abstractNum>
    
    In this case, the resulting paragraphs would inherit the properties of the abstract numbering definition levels with ilvl attributes of 0 and 1, respectively. end example]
    
    
    ??? abstract "Attributes"
    
        val (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.4 isLgl (使用阿拉伯数字显示所有级别)

**isLgl (Display All Levels Using Arabic Numerals)**

=== "中文"
    
    此元素指定是否应将给定编号级别的所有显示级别的文本使用十进制数格式显示，而不论该级别在列表中的实际编号格式如何。【注意：这种编号样式通常称为法律编号样式。注意结束】
    
    如果存在此元素，那么在显示此级别的编号格式时，lvlTxt 元素（[§17.9.11]）中的所有编号级别都将转换为其十进制等价物。如果省略此元素，那么每个级别将使用该级别的 numFmt（[§17.9.17]）显示。
    
    【示例：请考虑以下编号集。在这个空白编号段落集中，使用了三个编号级别，并且第三个级别应用了 isLgl 属性，结果如下：
    
    ![123](./imgs/17img44.png)
    
    如上所示，列表中第三级别的每个编号都已转换为其十进制等价物。启用第三编号级别法律编号规则所需的 WordprocessingML 如下：
    
    ```xml
    <w:lvl w:ilvl="2">
        …
        <w:isLgl />
        …
    </w:lvl>
    ```
    
    示例结束】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies whether or not all levels displayed for a given numbering level's text shall be displayed using the decimal number format, regardless of the actual number format of that level in the list. [Note: This numbering style is often referred to as the legal numbering style. end note]
    
    
    If this element is present, then all numbering levels present in the lvlTxt element ([§17.9.11]) shall be converted to their decimal equivalents when they are displayed in this level in the numbering format. If this element is omitted, then each level is displayed using the numFmt ([§17.9.17]) of that level.
    
    [Example: Consider the numbering set below. In this set of blank numbered paragraphs, three numbering levels have been used and the third has the isLgl property applied, resulting in the following:
    
    ![123](./imgs/17img44.png)
    
    As shown above, each number in the third level in the list has been converted to its decimal equivalent. The WordprocessingML necessary to turn on the legal numbering rule for the third numbering level is given below:
    
    ```xml
    <w:lvl w:ilvl="2">
        …
        <w:isLgl />
        …
    </w:lvl>
    ```
    
    end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

## 17.9.5 lvl (编号级别覆盖定义)

**lvl (Numbering Level Override Definition)**

=== "中文"
    
    此元素指定使用 lvlOverride 元素（[§17.9.8]）定义的特定编号级别在给定编号级别定义覆盖中的外观和行为。
    
    编号级别覆盖定义与编号级别定义相同，不同之处在于它是使用 num 元素（[§17.9.15]）作为编号定义实例的一部分定义的，而不是使用 abstractNum 元素（[§17.9.1]）作为抽象编号定义的一部分。
    
    【示例：请考虑一个编号定义实例，它从 abstractNumId 为 4 的抽象编号定义继承信息，但应为编号定义的级别 0 使用一组不同的属性。生成的 WordprocessingML 如下所示：

    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    此编号定义实例用指定的编号级别覆盖定义覆盖了列表的级别 0，替换了抽象编号级别定义中的那些属性。示例结束】
    
    【注意：设置级别覆盖的能力优化了 WordprocessingML 中编号的使用，因为它避免了在编号集稍有不同的情况下写出冗余的抽象编号定义。
    
    请考虑使用 WordprocessingML 创建两个编号集，它们仅在第一级编号级别的外观和样式上有所不同。只要每个编号集引用不同的编号定义实例，其中一个编号定义实例利用第一级编号级别的级别覆盖，这两个编号集都可以使用相同的抽象编号定义。下面是展示这一点的 WordprocessingML：

    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4" />
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
        <w:lvl w:ilvl="0">
            <w:start w:val="4" />
            <w:lvlText w:val="%1)" />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:ind w:start="360" w:hanging="360" />
            </w:pPr>
        </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    注意结束】
    
    
    ??? abstract "Attributes"
    
        **ilvl**（编号级别）
        
        :   指定由这组编号属性定义的编号级别定义。
        
            此覆盖是文档中列表级别数量的零起始索引。【示例：值为 2 表示文档中的第三个列表级别。示例结束】
        
            【示例：请考虑以下编号定义实例的 WordprocessingML：
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                …
                </w:lvlOverride>
            </w:num>
            ```
            
            在此示例中，被引用的抽象编号定义中的第一个编号级别定义（具有 ilvl 为 0）被覆盖。示例结束】
            
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
        
        **tentative**（临时编号）
        
        :   指定给定编号级别已由生产者保存，但未在父文档中使用。这意味着该编号级别可以由未来的消费者重新定义，而不会更改文档的实际内容。
        
            对于此属性值，值为 1 或 true 表示该编号级别未在当前文档内容中使用。
            
            对于此属性值，值为 0 或 false 表示该编号级别已在父文档中使用，且不能重新定义而不更改其内容。这是此属性的默认值，在省略此属性时隐含。
            
            【示例：考虑以下 WordprocessingML 编号级别：
            
            ```xml
            <w:lvl w:ilvl="0" w:tentative="true" >
            …
            </w:lvl>
            ```
            
            此级别的 tentative 属性设置为 true，因此此编号级别的内容尚未在文档中使用，可以由消费者根据需要重新定义。示例结束】
            
            
            如果此属性等于 1 或 true，则给定文档的 WordprocessingML 包含与此编号级别相关联的编号级别信息，但“tentative”编号级别将不会在任何与编号级别相关的宿主应用程序用户界面中表示。
        
            此属性的可能值由 ST_OnOff 简单类型定义（[§22.9.2.7]）。
        
        **tplc**（模板代码）
        
        :   指定一个唯一的十六进制值，可用于指定应在应用程序用户界面中显示此编号级别的位置。该值的解释方法由应用程序定义。
        
            如果省略了此属性，则此编号可以显示在消费者选择的任何位置。
        
            【示例：考虑以下抽象编号定义：
            
            ```xml
            <w:abstractNum w:abstractNumId="1" >
            …
            </w:abstractNum>
            ```
            
            在此示例中，具有 abstractNumId 属性值为 1 的 abstractNum 元素将显示在由模板代码 04090019 指定的消费者应用程序用户界面内的区域中。示例结束】
            
            此属性的可能值由 ST_LongHexNumber 简单类型定义（[§17.18.50]）。
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lvl) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies the appearance and behavior of a specific numbering level within a given numbering level definition override defined using the lvlOverride element ([§17.9.8]).
    
    A numbering level override definition is identical to a numbering level definition, except for the fact that it is defined as part of a numbering definition instance using the num element ([§17.9.15]) rather than as part of an abstract numbering definition using the abstractNum element ([§17.9.1]).
    
    [Example: Consider a numbering definition instance which inherits its information from the abstract numbering definition with abstractNumId of 4, but should use a different set of properties for level 0 of the numbering definition. The resulting WordprocessingML would look like:
    
    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    This numbering definition instance overrides level 0 of the list with the specified numbering level override definition, replacing those in the abstract numbering level definition. end example]
    
    [Note: The ability to set level overrides optimizes use of numbering in WordprocessingML as it prevents writing out redundant abstract numbering definitions if numbering sets only slightly differ.
    
    Consider using WordprocessingML to create two numbered sets that only differ only in the appearance and style of the first numbering level. Both could use the same abstract numbering definition as long as each references a different numbering definition instance with one of the numbering definition instances leveraging a level override for the first numbering level. Below is WordprocessingML that illustrates this:
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4" />
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
        <w:lvl w:ilvl="0">
            <w:start w:val="4" />
            <w:lvlText w:val="%1)" />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:ind w:start="360" w:hanging="360" />
            </w:pPr>
        </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    end note]
    
    
    ??? abstract "Attributes"
    
        **ilvl** (Numbering Level)
    
        :   Specifies the numbering level definition that is to be defined by this set of numbering properties.
    
            This override is a zero-based index of the number of list levels in the document. [Example: A value of 2 is the 3rd list level in the document. end example]
            
            [Example: Consider the following WordprocessingML for a numbering definition instance:
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                …
                </w:lvlOverride>
            </w:num>
            ```
            
            In this example, the first numbering level definition (with an ilvl of 0) within the referenced abstract numbering definition is overridden. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
        **tentative** (Tentative Numbering)
    
        :   Specifies that a given numbering level was been saved by a producer but was not used in the parent document. This means that this numbering level can be redefined by a future consumer without changing the actual content of the document.
    
            A value of 1 or true for this attribute value specifies that the numbering level is not used in the current document's contents.
            
            A value of 0 or false for this attribute value specifies that the numbering level is used in the parent document and cannot be redefined without changing its contents. This is the default value for this attribute, and is implied when this attribute is omitted.
            
            [Example: Consider the following WordprocessingML numbering level:
            
            ```xml
            <w:lvl w:ilvl="0" w:tentative="true" >
            …
            </w:lvl>
            ```
            
            This level has the tentative attribute set to true, therefore the contents of this numbering level have not been used in the document and can be redefined by a consumer as desired. end example]
            
            
            If this attribute is equal to 1 or true, the WordprocessingML for a given document contains the numbering level information associated with this numbering level, but the 'tentative' numbering level(s) shall not be represented in any of the hosting application's user interface pertaining to numbering levels.
    
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
        
        **tplc** (Template Code)
    
        :   Specifies a unique hexadecimal value which can be used to specify a location within an application's user interface in which this numbering level shall be displayed. The method by which this value is interpreted shall be application-defined.
            
            If this attribute is omitted, then this numbering can be displayed in any location chosen by the consumer.
            
            [Example: Consider the following abstract numbering definition:
            
            ```xml
            <w:abstractNum w:abstractNumId="1" >
            …
            </w:abstractNum>
            ```
            
            In this example the abstractNum element with attribute abstractNumId equal to 1, would appear in the area within a consumer's application user interface specified by the template code 04090019.end example]
            
            The possible values for this attribute are defined by the ST_LongHexNumber simple type ([§17.18.50]).
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lvl) is located in §A.1. end note]

## 17.9.6 lvl (编号级别定义)

**lvl (Numbering Level Definition)**

=== "中文"
    
    该元素指定了在给定抽象编号定义中编号级别的外观和行为。编号级别包含一组属性，用于在抽象编号定义中为给定的编号级别显示编号。
    
    编号级别定义与编号级别覆盖定义相同，不同之处在于它是作为编号定义实例的一部分使用 abstractNum 元素（[§17.9.1]）而不是作为抽象编号定义的一部分使用 num 元素（[§17.9.15]）来定义的。
    
    【示例：考虑以下 WordprocessingML 示例：
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="1DE04504" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:lvl w:ilvl="0" w:tplc="0409000F">
            …
        </w:lvl>
        <w:lvl w:ilvl="1" w:tplc="04090019">
            …
        </w:lvl>
        <w:lvl w:ilvl="2" w:tplc="04090019">
            …
        </w:lvl>
        <w:lvl w:ilvl="3" w:tplc="0409000F">
            …
        </w:lvl>
        …
    </w:abstractNum>
    ```
    
    该示例表明，任何使用具有属性 val 设置为 0、1、2 或 3 的 ilvl 元素的编号属性的段落，其外观和行为与上述给定的 lvl 元素指定的其前四个编号级别相对应（假设未指定级别覆盖）。示例结束】
    
    
    ??? abstract "Attributes"
    
        **ilvl**（编号级别）
        
        :   指定由这组编号属性定义的编号级别。
        
            此覆盖是文档中列表级别数量的零起始索引。
            
            【示例：值为 2 表示文档中的第三个列表级别。示例结束】
            
            【示例：考虑以下用于编号定义实例的 WordprocessingML：
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                    …
                </w:lvlOverride>
            </w:num>
            ```
            
            在此示例中，被引用的抽象编号定义中的第一个编号级别定义（具有 ilvl 为 0）被覆盖。示例结束】
            
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
        
        **tentative**（临时编号）
        
        :   指定给定编号级别已由生产者保存，但未在父文档中使用。这意味着该编号级别可以由未来的消费者重新定义，而不会更改文档的实际内容。
        
            对于此属性值，值为 1 或 true 表示该编号级别未在当前文档内容中使用。
            
            对于此属性值，值为 0 或 false 表示该编号级别已在父文档中使用，且不能重新定义而不更改其内容。这是此属性的默认值，在省略此属性时隐含。
            
            【示例：考虑以下 WordprocessingML 编号级别：
            
            ```xml
            <w:lvl w:ilvl="0" w:tentative="true" >
            …
            </w:lvl>
            ```
            
            此级别的 tentative 属性设置为 true，因此此编号级别的内容尚未在文档中使用，可以由消费者根据需要重新定义。示例结束】
            
            
            如果此属性等于 1 或 true，则给定文档的 WordprocessingML 包含与此编号级别相关联的编号级别信息，但“tentative”编号级别将不会在任何与编号级别相关的宿主应用程序用户界面中表示。
        
            此属性的可能值由 ST_OnOff 简单类型定义（[§22.9.2.7]）。
        
        **tplc**（模板代码）
        
        :   指定一个唯一的十六进制值，可用于指定应在应用程序用户界面中显示此编号级别的位置。该值的解释方法由应用程序定义。
        
            如果省略了此属性，则此编号可以显示在消费者选择的任何位置。
        
            【示例：考虑以下抽象编号定义：
            
            ```xml
            <w:abstractNum w:abstractNumId="1" >
            …
            </w:abstractNum>
            ```
            
            在此示例中，具有 abstractNumId 属性值为 1 的 abstractNum 元素将显示在由模板代码 04090019 指定的消费者应用程序用户界面内的区域中。示例结束】
            
            此属性的可能值由 ST_LongHexNumber 简单类型定义（[§17.18.50]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lvl) is located in §A.1. end note]

=== "英文"
    
    This element specifies the appearance and behavior of a numbering level within a given abstract numbering definition. A numbering level contains a set of properties for the display of the numbering for a given numbering level within an abstract numbering definition.
    
    A numbering level definition is identical to a numbering level override definition, except for the fact that it is defined as part of a numbering definition instance using the abstractNum element ([[§17.9.1]]) rather than as part of an abstract numbering definition using the num element ([§17.9.15]).
    
    [Example: Consider the WordprocessingML below:
    
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="1DE04504" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:lvl w:ilvl="0" w:tplc="0409000F">
            …
        </w:lvl>
        <w:lvl w:ilvl="1" w:tplc="04090019">
            …
        </w:lvl>
        <w:lvl w:ilvl="2" w:tplc="04090019">
            …
        </w:lvl>
        <w:lvl w:ilvl="3" w:tplc="0409000F">
            …
        </w:lvl>
        …
    </w:abstractNum>
    ```
    
    This example shows that any paragraph whose numbering properties use the ilvl elements with the attribute val set equal to 0, 1, 2, or 3 has the appearance and behavior of their first four numbered levels specified by the lvl elements given above (assuming that no level overrides have been specified). end example]
    
    
    ??? abstract "Attributes"
    
        **ilvl** (Numbering Level)
    
        :   Specifies the numbering level definition that is to be defined by this set of numbering properties.
    
            This override is a zero-based index of the number of list levels in the document.
            
            [Example: A value of 2 is the 3rd list level in the document. end example]
            
            [Example: Consider the following WordprocessingML for a numbering definition instance:
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                    …
                </w:lvlOverride>
            </w:num>
            ```
            
            In this example, the first numbering level definition (with an ilvl of 0) within the referenced abstract numbering definition is overridden. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
        
        **tentative** (Tentative Numbering)
    
        :   Specifies that a given numbering level was been saved by a producer but was not used in the parent document. This means that this numbering level can be redefined by a future consumer without changing the actual content of the document.
    
            A value of 1 or true for this attribute value specifies that the numbering level is not used in the current document's contents.
            
            A value of 0 or false for this attribute value specifies that the numbering level is used in the parent document and cannot be redefined without changing its contents. This is the default value for this attribute, and is implied when this attribute is omitted.
            
            [Example: Consider the following WordprocessingML numbering level:
            
            ```xml
            <w:lvl w:ilvl="0" w:tentative="true" >
            …
            </w:lvl>
            ```
            
            This level has the tentative attribute set to true, therefore the contents of this numbering level have not been used in the document and can be redefined by a consumer as desired. end example]
            
            
            If this attribute is equal to 1 or true, the WordprocessingML for a given document contains the numbering level information associated with this numbering level, but the 'tentative' numbering level(s) shall not be represented in any of the hosting application's user interface pertaining to numbering levels.
    
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
            
        **tplc** (Template Code)
    
        :   Specifies a unique hexadecimal value which can be used to specify a location within an application's user interface in which this numbering level shall be displayed. The method by which this value is interpreted shall be application-defined.
            
            If this attribute is omitted, then this numbering can be displayed in any location chosen by the consumer.
            
            [Example: Consider the following abstract numbering definition:
            
            ```xml
            <w:abstractNum w:abstractNumId="1" >
            …
            </w:abstractNum>
            ```
            
            In this example the abstractNum element with attribute abstractNumId equal to 1, would appear in the area within a consumer's application user interface specified by the template code 04090019.end example]
            
            The possible values for this attribute are defined by the ST_LongHexNumber simple type ([§17.18.50]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lvl) is located in §A.1. end note]

## 17.9.7 lvlJc (理由)

**lvlJc (Justification)**

=== "中文"
    
    该元素指定在给定编号级别中使用的文本的对齐方式。
    
    此对齐是相对于文档中父编号段落的文本边距应用的。
    
    如果省略，则段落将相对于文本边距左对齐（对于从左到右的段落），并相对于文本边距右对齐（对于从右到左的段落）。
    
    【示例：考虑下面定义的编号级别：
    
    ```xml
    <w:lvl w:ilvl="8" w:tplc="756C1446" w:tentative="1">
        <w:start w:val="1" />
        <w:numFmt w:val="bullet" />
        <w:lvlText w:val="•" />
        <w:lvlJc w:val="start" />
        …
    </w:lvl>
    ```
    
    在此编号级别中，给定的编号符号相对于文本边距左对齐，因此编号从文本边距向左延伸至文本（假设是从左到右的段落）。示例结束】
    
    编号级别的文本是由 lvlText 元素（[§17.9.11]）定义的用于创建编号段落的数字、符号、字符、图形等。
    
    【示例：考虑以下编号段落：
    
    1) 示例一
    a. 示例二
    • 示例三
    
    这三个编号段落中的编号符号分别是“1”、“a”和“•”。示例结束】
    
    ??? abstract "属性"
    
        **val**（对齐类型）
    
        :   指定应应用于文档中父对象的对齐方式。
    
            此属性的可能值（见下文）始终指定了相对于段落的前沿的对齐方式，因此在从右到左和从左到右的文档之间的语义会发生变化。
            
            【示例：考虑以下用于文档中段落的 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
            <w:jc w:val="end" />
            </w:pPr>
            ```
            
            对于从左到右的段落，此段落现在在页面上右对齐，在从右到左的段落中左对齐。示例结束】
            
            此属性的可能值由 ST_Jc 简单类型定义（[§17.18.44]）。
        
    [Note: The W3C XML Schema definition of this element’s content model (CT_Jc) is located in §A.1. end note]

=== "英文"
    
    This element specifies the type of justification used on a numbering level's text within a given numbering level.
    
    This justification is applied relative to the text margin of the parent numbered paragraph in the document.
    
    If omitted, the paragraph shall have left justification relative to the text margin in left-to-right paragraphs, and right justification relative to the text margin in right-to-left paragraphs.
    
    [Example: Consider the numbering level defined below:
    
    ```xml
    <w:lvl w:ilvl="8" w:tplc="756C1446" w:tentative="1">
        <w:start w:val="1" />
        <w:numFmt w:val="bullet" />
        <w:lvlText w:val="•" />
        <w:lvlJc w:val="start" />
        …
    </w:lvl>
    ```
    
    In this numbering level, the given numbering symbol is left justified with respect to the text margin, therefore the numbering extends left from the text margin towards the text (assuming a left-to-right paragraph). end example]
    
    A numbering level's text is the numeral, symbol, character, graphic, etc. used to create a numbered paragraph as defined by the lvlText element ([§17.9.11]).
    
    [Example: Consider the numbered paragraphs below:
    
    1) Example one
    a. Example two
    • Example three
    
    The numbering symbol in these three numbered paragraphs are "1", "a", and "•", respectively. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Alignment Type)
    
        :   Specifies the justification which should be applied to the parent object within a document.
    
            The possible values (see below) for this attribute are always specified with left specifying justification relative to the leading edge of the paragraph, and therefore change semantic between right-to-left and left-to-right documents.
            
            [Example: Consider the following WordprocessingML fragment for a paragraph in a document:
            
            ```xml
            <w:pPr>
            <w:jc w:val="end" />
            </w:pPr>
            ```
            
            This paragraph is now right justified on the page for a left-to-right paragraph, left justified for a right-to-left paragraph. end example]
            
            The possible values for this attribute are defined by the ST_Jc simple type ([§17.18.44]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Jc) is located in §A.1. end note]

## 17.9.8 lvlOverride (编号级别定义覆盖)

**lvlOverride (Numbering Level Definition Override)**

=== "中文"
    
    该元素指定一个可选的覆盖，应用于给定编号定义实例的抽象编号定义中的零个或多个级别。每个此元素的实例用于覆盖给定抽象编号定义中的特定编号级别定义的外观和行为。
    
    【示例：考虑一个编号定义实例，该实例从抽象编号定义（abstractNumId 为 4）继承其信息，但希望对编号定义的级别 0 和级别 1 使用不同的属性。生成的 WordprocessingML 如下所示：
    
    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
        <w:lvlOverride w:ilvl="1">
            <w:lvl w:ilvl="1">
                <w:start w:val="5" />
                <w:lvlText w:val="%Test)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    示例结束】
    
    【注意：设置级别覆盖的能力可优化 WordprocessingML 中编号的使用，因为它可以防止在编号集仅略有不同的情况下写出冗余的抽象编号定义。
    
    考虑使用 WordprocessingML 创建两个编号集，它们在第一个编号级别的外观和样式上略有不同。只要每个引用不同的编号定义实例，并且其中一个编号定义实例利用级别覆盖来设置第一个编号级别，两者可以使用相同的抽象编号定义。以下是说明此示例的 WordprocessingML：
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4" />
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
        <w:lvl w:ilvl="0">
            <w:start w:val="4" />
            <w:lvlText w:val="%1)" />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:ind w:start="360" w:hanging="360" />
            </w:pPr>
        </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    注意结束】
    
    ??? abstract "Attributes"
    
        **ilvl**（编号级别 ID）
        
        :   指定要覆盖的给定抽象编号定义的编号级别。
        
            如果此数字与子级别（lvl 元素）的 ilvl 冲突，则后者将被忽略。
            
            [示例：考虑一个编号定义实例，该实例从抽象编号定义（abstractNumId 为 4）继承其信息，但希望对编号定义的级别 0 使用不同的属性。生成的 WordprocessingML 如下所示：
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                    <w:lvl w:ilvl="0">
                        <w:start w:val="4" />
                        <w:lvlText w:val="%1)" />
                        <w:lvlJc w:val="start" />
                        <w:pPr>
                            <w:ind w:left="360" />
                        </w:pPr>
                    </w:lvl>
                </w:lvlOverride>
            </w:num>
            ```
            
            此级别使用指定的编号属性覆盖了抽象编号定义的级别 0 属性，替换了抽象编号定义中的属性。示例结束]
            
            该属性的可能值由 ST_DecimalNumber 简单类型（[§17.18.10]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumLvl) is located in §A.1. end note]

=== "英文"
    
    This element specifies an optional override which shall be applied in place of zero or more levels from the abstract numbering definition for a given numbering definition instance. Each instance of this element is used to override the appearance and behavior of a given numbering level definition within the given abstract numbering definition.
    
    [Example: Consider a numbering definition instance which inherits its information from the abstract numbering definition with abstractNumId of 4, but wishes to use a different set of properties for level 0 and level 1 of the numbering definition. The resulting WordprocessingML would look like:
    
    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
        <w:lvlOverride w:ilvl="1">
            <w:lvl w:ilvl="1">
                <w:start w:val="5" />
                <w:lvlText w:val="%Test)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    end example]
    
    [Note: The ability to set level overrides optimizes use of numbering in WordprocessingML as it prevents writing out redundant abstract numbering definitions if numbering sets only slightly differ.
    
    Consider using WordprocessingML to create two numbered sets that only differ only in the appearance and style of the first numbering level. Both could use the same abstract numbering definition as long as each references a different numbering definition instance with one of the numbering definition instances leveraging a level override for the first numbering level. Below is WordprocessingML that illustrates this:
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4" />
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
        <w:lvl w:ilvl="0">
            <w:start w:val="4" />
            <w:lvlText w:val="%1)" />
            <w:lvlJc w:val="start" />
            <w:pPr>
                <w:ind w:start="360" w:hanging="360" />
            </w:pPr>
        </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    end note]
    
    ??? abstract "Attributes"
    
        **ilvl** (Numbering Level ID)
    
        :   Specifies the numbering level of a given abstract numbering definition to be overridden.
    
            If this number conflicts with the ilvl of the child lvl element, then the latter shall be ignored.
            
            [Example: Consider a numbering definition instance which inherits its information from the abstract numbering definition with abstractNumId of 4, but wishes to use a different set of properties for level 0 of the numbering definition. The resulting WordprocessingML would look like:
            
            ```xml
            <w:num w:numId="6">
                <w:abstractNumId w:val="4" />
                <w:lvlOverride w:ilvl="0">
                    <w:lvl w:ilvl="0">
                        <w:start w:val="4" />
                        <w:lvlText w:val="%1)" />
                        <w:lvlJc w:val="start" />
                        <w:pPr>
                            <w:ind w:left="360" />
                        </w:pPr>
                    </w:lvl>
                </w:lvlOverride>
            </w:num>
            ```
            
            This level overrides level 0 of the abstract numbering definition's level properties with the specified set of numbering properties, replacing those in the abstract numbering definition. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumLvl) is located in §A.1. end note]

## 17.9.9 lvlPicBulletId (图片编号符号定义参考)

**lvlPicBulletId (Picture Numbering Symbol Definition Reference)**

=== "中文"
    
    这个元素指定了一个图片，该图片将被用作给定编号级别的编号符号，通过引用图片编号符号定义的 numPictBullet 元素（[§17.9.20]）来实现。通过此元素的 val 属性进行此引用。
    
    图片将被添加到编号级别中，通过用此图片的一个实例替换 lvlText 中的每个字符。
    
    [示例：考虑以下 WordprocessingML，说明了 lvlPicBulletId 通过其 val 属性引用图片编号符号定义的方式：
    
    ```xml
    <w:numPicBullet w:numPicBulletId="1">
        <w:drawing>
        …
        </w:drawing>
    </w:numPicBullet>
    …
    <w:abstractNum w:abstractNumId="7">
        <w:nsid w:val="71A06359" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:tmpl w:val="10643FE6" />
        <w:lvl w:ilvl="0" w:tplc="B7663E56">
            <w:start w:val="1" />
            <w:numFmt w:val="bullet" />
            <w:lvlText w:val="AA" />
            <w:lvlPicBulletId w:val="1" />
        </w:lvl>
    </w:abstractNum>
    ```
    
    生成的编号必须由两个使用 numPicBullet 元素指定的图片实例组成。示例结束]
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
    
        :   指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下简单类型 ST_DecimalNumber 的数值 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。示例结束]
            
            此属性的可能值由 ST_DecimalNumber 简单类型（[§17.18.10]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies a picture which shall be used as a numbering symbol for a given numbering level by referring to a picture numbering symbol definition's numPictBullet element ([§17.9.20]). This reference is made through this element's val attribute.
    
    The picture shall be added to the numbering level by replacing each character in the lvlText with one instance of this image.
    
    [Example: Consider the WordprocessingML below illustrating how the lvlPicBulletId references a picture numbering symbol definition though its val attribute:
    
    ```xml
    <w:numPicBullet w:numPicBulletId="1">
        <w:drawing>
        …
        </w:drawing>
    </w:numPicBullet>
    …
    <w:abstractNum w:abstractNumId="7">
        <w:nsid w:val="71A06359" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:tmpl w:val="10643FE6" />
        <w:lvl w:ilvl="0" w:tplc="B7663E56">
            <w:start w:val="1" />
            <w:numFmt w:val="bullet" />
            <w:lvlText w:val="AA" />
            <w:lvlPicBulletId w:val="1" />
        </w:lvl>
    </w:abstractNum>
    ```
    
    The resulting numbering must consist of two instances of the image specified using the numPicBullet element. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]


## 17.9.10 lvlRestart (重新启动编号级别符号)

**lvlRestart (Restart Numbering Level Symbol)**

=== "中文"
    
    该元素指定了一个基于一的索引，用于确定何时重新开始编号级别到其起始值（[§17.9.25]）。当指定的编号级别的一个实例（它应该是高级别（比此级别早）或任何更早级别）在给定文档的内容中使用时，编号级别将重新开始。[示例：如果此值为2，则级别二和级别一都会重置此值。示例结束]
    
    如果省略了此元素，则编号级别将在每次使用前一个编号级别或任何更早级别时重新开始。如果指定的级别高于当前级别，则将忽略此元素。同样，值为0将指定此级别永远不会重新开始。
    
    [示例：考虑一个 WordprocessingML 文档中的一组编号段落，在该组中，级别 ilvl 为 2 的编号级别设置为永不重新开始：
    
    ```xml
    <w:lvl w:ilvl="0">
        <w:start w:val="1" />
        <w:lvlText w:val="%1)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="360" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    <w:lvl w:ilvl="1">
        <w:start w:val="1" />
        <w:numFmt w:val="upperLetter" />
        <w:lvlText w:val="%2)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="720" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    <w:lvl w:ilvl="2">
        <w:start w:val="1" />
        <w:numFmt w:val="lowerRoman" />
        <w:lvlRestart w:val="0">
        <w:lvlText w:val="%3)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="1080" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    ```
    
    生成的段落集合在每次级别一后（2之后）将级别二重新开始到其起始值，下一个级别二再次为a))，但级别三永远不会重新开始，并在使用级别二和一后继续到 iii)。示例结束]
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies a one-based index which determines when a numbering level should restart to its start value ([§17.9.25]). A numbering level restarts when an instance of the specified numbering level, which shall be higher (earlier than this level) or any earlier level is used in the given document's contents. [Example: If this value is 2, then both level two and level one reset this value. end example]
    
    If this element is omitted, the numbering level shall restart each time the previous numbering level or any earlier level is used. If the specified level is higher than the current level, then this element shall be ignored. As well, a value of 0 shall specify that this level shall never restart.
    
    [Example: Consider a set of numbered paragraphs in a WordprocessingML document where numbering level with ilvl of 2 is set to never restart:
    
    ```xml
    <w:lvl w:ilvl="0">
        <w:start w:val="1" />
        <w:lvlText w:val="%1)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="360" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    <w:lvl w:ilvl="1">
        <w:start w:val="1" />
        <w:numFmt w:val="upperLetter" />
        <w:lvlText w:val="%2)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="720" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    <w:lvl w:ilvl="2">
        <w:start w:val="1" />
        <w:numFmt w:val="lowerRoman" />
        <w:lvlRestart w:val="0">
        <w:lvlText w:val="%3)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="1080" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    ```
    
    The resulting set of paragraphs has level two restarting to its start value after each level one (after 2), the next level two is again a)), but level three never restarts and continues at iii) even after the use of a level two and one. end example]
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.11 lvlText (编号级别文本)

**lvlText (Numbering Level Text)**

=== "中文"
    
    该元素指定了在显示具有给定编号级别的段落时应显示的文本内容。
    
    此元素的 val 属性中的所有文本都将被视为要在每个此编号级别的实例中重复的文字文本，除了任何使用百分号（%）后跟数字的情况，该百分号后的数字用于指示在此级别使用的基于一的编号的索引。任何比此级别高的级别的数字都将被忽略。
    
    当使用 % 语法时，数字将针对该级别的每个后续段落（无论是否连续）递增，直到在两个后续段落之间看到重新开始级别为止。
    
    [示例：考虑以下用于编号级别的 WordprocessingML：
    
    ```xml
    <w:lvl w:ilvl="1">
    …
    <w:lvlText w:val="字符串A %2 字符串B %1 字符串C %3"/>
    …
    </w:lvl>
    ```
    
    这指定了三个字符串（字符串A、字符串B、字符串C）必须与级别二（ilvl 为 1）的编号一起作为字符串文字使用，同时还要使用级别一和级别零的编号符号。尽管此处还引用了级别二，但由于它是高于当前编号级别的级别，因此将其忽略。
    
    因此，假设级别零使用的编号符号是阿拉伯数字，级别一使用的编号符号是罗马数字，使用此 WordprocessingML 编号集的一组编号段落必须输出为：
    
    ![123](./imgs/17img45.png)
    
    其中 %1 和 %2 的值分别对应于级别零和级别一的当前编号符号值。示例结束]
    
    ??? abstract "Attributes"
    
        **null**（级别文本为空字符）
        
        :   指定空字符应作为给定编号级别的编号符号。
        
            如果 val 属性包含任何内容，则应忽略此属性。
            
            如果省略此属性，则不应使用空字符串替代空字符串。【注意：空字符与空字符串不同。结束注意】
            
            [示例：考虑以下 WordprocessingML：
            
            ```xml
            <w:lvl w:ilvl="1">
                …
                <w:lvlText w:null="on" />
                …
            </w:lvl>
            ```
        
            此级别文本由单个空字符组成，而不是空字符串，因为设置了 null 属性。示例结束】
            
            此属性的可能值由 ST_OnOff 简单类型定义（[§22.9.2.7]）。
        
        **val**（级别文本）
        
        :   指定在文档内容中引用编号级别时要使用的实际文本。
        
            如果未指定此属性，则应将空字符串用作级别的文本。
            
            [示例：考虑以下 WordprocessingML：
            
            ```xml
            <w:lvl w:ilvl="1">
                …
                <w:lvlText w:val="test" />
                …
            </w:lvl>
            ```
            
            这里 val 属性指定了文字字符串 test 作为给定编号级别的文本，无论其位置如何。示例结束】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LevelText) is located in §A.1. end note]

=== "英文"
    
    This element specifies the textual content which shall be displayed when displaying a paragraph with the given numbering level.
    
    All text in this element's val attribute shall be taken as literal text to be repeated in each instance of this numbering level, except for any use of the percent symbol (%) followed by a number, which shall be used to indicate the one-based index of the number to be used at this level. Any number of a level higher than this level shall be ignored. 
    
    When the % syntax is used, the number shall be incremented for each subsequent paragraph of that level (sequential or not), until the restart level is seen between two subsequent paragraphs of this level.
    
    [Example: Consider the following WordprocessingML for a numbering level:
    
    ```xml
    <w:lvl w:ilvl="1">
    …
    <w:lvlText w:val="StringA %2 StringB %1 StringC %3"/>
    …
    </w:lvl>
    ```
    
    This specifies that three strings (StringA, StringB, StringC) must be used as string literals in the numbering for level two (ilvl of 1) along with the numbering symbol used for level one and level zero. Although level two is also referenced here, it is ignored as it is a higher level than the current numbering level. 
    
    Therefore, assuming the numbering symbol used by numbering level zero is an Arabic numeral, and the numbering symbol used by numbering level one is a Roman numeral, a set of numbered paragraphs using this WordprocessingML numbering set must be output as:
    
    ![123](./imgs/17img45.png)
    
    with the %1 and %2 values corresponding to the current numbering symbol value for numbering level zero and one, respectively. end example]
    
    ??? abstract "Attributes"
    
        **null** (Level Text Is Null Character)
    
        :   Specifies that a null character shall be used as the numbering symbol for a given numbering level.
    
            If the val attribute contains any content, then this attribute shall be ignored.
            
            If this attribute is omitted, then the null string shall not be used in place of the empty string. [Note: A null character is different from an empty string. end note]
            
            [Example: Consider the WordprocessingML below:
            
            ```xml
            <w:lvl w:ilvl="1">
                …
                <w:lvlText w:null="on" />
                …
            </w:lvl>
            ```
    
            This level text consists of a single null character, and not the empty string, as the null attribute is set. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
        
        **val** (Level Text)
    
        :   Specifies the actual text to be used for the numbering level when it is referenced in the document's content.
    
            If this attribute is not specified, then the empty string shall be used as the level's text.
            
            [Example: Consider the WordprocessingML below:
            
            ```xml
            <w:lvl w:ilvl="1">
                …
                <w:lvlText w:val="test" />
                …
            </w:lvl>
            ```
            
            Here the val attribute specifies that the literal string test is to be surfaced as the text for the given numbering level, regardless of its position. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LevelText) is located in §A.1. end note]

## 17.9.12 multiLevelType (抽象编号定义类型)

**multiLevelType (Abstract Numbering Definition Type)**

=== "中文"
    
    这个元素指定了由给定抽象编号类型定义的编号类型。此信息仅用于由消费者确定此编号定义的用户界面行为，并不用于限制列表的行为（即，将多个级别标记为单级别的列表不会阻止使用第2至第9级别）。
    
    如果省略此元素，则假定列表为消费者所需的任何编号类型。
    
    [示例：考虑以下 WordprocessingML：
    
    ```xml
    <w:abstractNum w:abstractNumId="8">
        …
        <w:multiLevelType w:val="singleLevel" />
        …
    </w:abstractNum>
    ```
    
    通过 multiLevelType 元素，此抽象编号定义被指定为 singleLevel 编号类型。示例结束]
    
    ??? abstract "属性"
    
        **val**（抽象编号定义类型）
    
        :   指定由给定抽象编号定义启用的特定编号类型。
    
            [示例：考虑以下 WordprocessingML：
            
            ```xml
            <w:abstractNum w:abstractNumId="8">
                …
                <w:multiLevelType w:val="multilevel" />
                …
            </w:abstractNum>
            ```
            
            此抽象编号定义被指定为多级编号类型，消费者可以使用该类型将此编号正确放置在用户界面中。示例结束]
            
            此属性的可能值由 ST_MultiLevelType 简单类型定义（[§17.18.58]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MultiLevelType) is located in §A.1. end note]

=== "英文"
    
    This element specifies the type of numbering defined by a given abstract numbering type. This information shall only be used by a consumer to determine user interface behaviors for this numbering definition, and shall not be used to limit the behavior of the list (i.e. a list with multiple levels marked as singleLevel shall not be prevented from using levels 2 through 9).
    
    If this element is omitted, then the list shall be assumed to be of any numbering type desired by the consumer.
    
    [Example: Consider the WordprocessingML below:
    
    ```xml
    <w:abstractNum w:abstractNumId="8">
        …
        <w:multiLevelType w:val="singleLevel" />
        …
    </w:abstractNum>
    ```
    
    This abstract numbering definition is specified to be of the singleLevel numbering type by the multiLevelType element. end example]
    
    ??? abstract "Attributes"
    
        **val** (Abstract Numbering Definition Type)
    
        :   Specifies the specific type of numbering enabled by a given abstract numbering definition.
    
            [Example: Consider the WordprocessingML below:
            
            ```xml
            <w:abstractNum w:abstractNumId="8">
                …
                <w:multiLevelType w:val="multilevel" />
                …
            </w:abstractNum>
            ```
            
            This abstract numbering definition is specified to be of the multilevel numbering type, which can be used by consumers to place this numbering correctly within a user interface. end example]
            
            The possible values for this attribute are defined by the ST_MultiLevelType simple type ([§17.18.58]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_MultiLevelType) is located in §A.1. end note]

## 17.9.13 name (摘要编号定义名称)

**name (Abstract Numbering Definition Name)**

=== "中文"
    
    这个元素指定了给定抽象编号定义的名称。该名称可用于提供给定编号定义的用户友好别名，但不应影响列表的行为 - 具有不同 name 元素的两个相同定义应该表现相同。
    
    如果省略此元素，则此抽象编号定义将没有名称。
    
    [示例：考虑以下 WordprocessingML：
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="5C294B5B" />
        <w:multiLevelType w:val="multilevel" />
        <w:tmpl w:val="6F8A81B0" />
        <w:name w:val="Example Name" />
        …
    </w:abstractNum>
    ```
    
    在此示例中，通过 name 元素，给定的抽象编号定义被命名为 Example Name。示例结束]
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
            
            但是，请考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，值都是在父元素的上下文中解释的。示例结束]
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the name of a given abstract numbering definition. This name can be surfaced in order to provide a user friendly alias for a given numbering definition, but shall not influence the behavior of the list - two identical definitions with different name elements shall behave identically.
    
    If this element is omitted, then this abstract numbering definition shall have no name.
    
    [Example: Consider the WordprocessingML below:
    
    ```xml
    <w:abstractNum w:abstractNumId="4">
        <w:nsid w:val="5C294B5B" />
        <w:multiLevelType w:val="multilevel" />
        <w:tmpl w:val="6F8A81B0" />
        <w:name w:val="Example Name" />
        …
    </w:abstractNum>
    ```
    
    In this example, the given abstract numbering definition is named Example Name by use of the name element. end example]
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            
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

## 17.9.14 nsid (抽象编号定义标识符)

**nsid (Abstract Numbering Definition Identifier)**

=== "中文"
    
    这个元素将一个唯一的十六进制 ID 关联到父抽象编号定义。对于两个基于相同初始编号定义的抽象编号定义，这个编号应该是相同的 - 如果一个文档被重新制作并且底层编号定义被更改，它应该保持其原始的 nsid。
    
    如果省略此元素，则列表将没有 nsid，生产者可以任意添加一个。
    
    【注：此元素可用于确定要应用于从一个文档复制并粘贴到另一个文档的带编号段落的抽象编号定义。考虑一个这样的情况：一个与 nsid 为 FFFFFF23 的抽象编号定义相关联的给定带编号段落，被粘贴到了与完全不同外观和 nsid 为 FFFFFF23 的抽象编号定义相关联的带编号段落之间。在这种情况下，由于相同的 nsid 值所启用的区别，主机应用程序不必随意保留被粘贴的带编号段落与其原始抽象编号定义相关联，因为它可以使用抽象编号定义的相同 nsid 值提供的信息来知道这两个编号集是相同的，并将段落合并到目标编号格式中。结束注】
    
    【示例：考虑以下抽象编号定义的 WordprocessingML：
    
    ```xml
    <w:abstractNum w:abstractNumId="3">
        <w:nsid w:val="FFFFFF89" />
        <w:multiLevelType w:val="singleLevel" />
        <w:tmpl w:val="D9842532" />
        …
    </w:abstractNum>
    ```
    
    在这个例子中，给定的抽象编号定义与唯一的十六进制 ID FFFFFF89 相关联。示例结束】
    
    ??? abstract "属性"
    
        **val**（长十六进制数值）
    
        :   指定一个数值，指定为一个四位十六进制数），这个十进制数的内容根据父 XML 元素的上下文进行解释。
    
            [示例：考虑简单类型 ST_LongHexNumber 的属性值：00BE2C6C。
            
            这个值是允许的，因为它包含四个十六进制数字，每个都是实际十进制数值的一个字节的编码。因此，它可以根据父 XML 元素的上下文进行解释。示例结束]
            
            此属性的可能值由简单类型 ST_LongHexNumber 定义（[§17.18.50]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LongHexNumber) is located in §A.1. end note]

=== "英文"
    
    This element associates a unique hexadecimal ID to the parent abstract numbering definition. This number shall be identical for two abstract numbering definitions that are based from the same initial numbering definition - if a document is repurposed and the underlying numbering definition is changed, it shall maintain its original nsid.
    
    If this element is omitted, then the list shall have no nsid and one can be added by a producer arbitrarily.
    
    [Note: This element can be used to determine the abstract numbering definition to be applied to a numbered paragraph copied from one document and pasted into another. Consider a case in which a given numbered paragraph associated with a abstract numbering definition with nsid FFFFFF23, is pasted among numbered paragraphs associated with a completely different appearance and an abstract numbering definition with an nsid of FFFFFF23. Here, because of the distinction enabled by the identical nsid values, the hosting application would not have to arbitrarily keep the pasted numbered paragraph associated with its original abstract numbering definition, as it might use the information provided by the abstract numbering definition's identical nsid values to know that those two numbering sets are identical, and merge the paragraphs into the target numbering format. end note]
    
    [Example: Consider the WordprocessingML for an abstract numbering definition below:
    
    ```xml
    <w:abstractNum w:abstractNumId="3">
        <w:nsid w:val="FFFFFF89" />
        <w:multiLevelType w:val="singleLevel" />
        <w:tmpl w:val="D9842532" />
        …
    </w:abstractNum>
    ```
    
    In this example, the given abstract numbering definition is associated with the unique hexadecimal ID FFFFFF89. end example]
    
    ??? abstract "Attributes"
    
        **val** (Long Hexadecimal Number Value)
    
        :   Specifies a number value specified as a four digit hexadecimal number), whose contents of this decimal number are interpreted based on the context of the parent XML element.
    
            [Example: Consider the following value for an attribute of simple type ST_LongHexNumber: 00BE2C6C.
            
            This value is permitted, as it contains four hexadecimal digits, each an encoding of an octet of the actual decimal number value. It can therefore be interpreted as desired in the context of the parent XML element, end example]
            
            The possible values for this attribute are defined by the ST_LongHexNumber simple type ([§17.18.50]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LongHexNumber) is located in §A.1. end note]

## 17.9.15 num (编号定义实例)

**num (Numbering Definition Instance)**

=== "中文"
        
    这个元素指定了一个唯一的编号信息实例，可以被父 WordprocessingML 文档中的零个或多个段落引用。
    
    此实例需要通过 abstractNumId 子元素（[§17.9.2]）引用基本抽象编号定义。此元素还可以用于指定应用于从此实例继承的抽象编号定义中的零个或多个级别的一组可选覆盖，通过可选的 lvlOverride 子元素（[§17.9.8]）。
    
    【示例：考虑一个包含四个编号定义实例的文档的 WordprocessingML，其中有两个引用相同的底层抽象编号定义：
    
    ```xml
    <w:numbering>
        …
        <w:num w:numId="2">
            <w:abstractNumId w:val="0" />
        </w:num>
        <w:num w:numId="3">
            <w:abstractNumId w:val="1" />
        </w:num>
        <w:num w:numId="4">
            <w:abstractNumId w:val="4" />
        </w:num>
        <w:num w:numId="5">
            <w:abstractNumId w:val="4" />
        </w:num>
    </w:numbering>
    ```
    
    如上所示，前两个编号定义实例分别引用了 abstractNumId 值为 0 和 1 的抽象编号定义，而最后两个都引用了抽象编号定义的 abstractNumId 为 4。示例结束】
    
    【示例：考虑一个编号定义实例，它从抽象编号定义的 abstractNumId 为 4 的编号信息中继承了其信息，但希望对编号定义的级别 0 使用不同的属性集。生成的 WordprocessingML 如下所示：
    
    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    lvlOverride 元素指定了抽象编号定义级别 0 的覆盖。示例结束】
    
    ??? abstract "Attributes"
    
        **numId**（编号定义实例 ID）
        
        :   指定一个唯一的ID，任何希望继承这些编号属性的编号段落都应使用 numPr 元素（[§17.3.1.19]）进行引用。
        
            【示例：考虑以下用于示例编号段落的 WordprocessingML：
            
            ```xml
            <w:p>
                <w:pPr>
                    <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                    </w:numPr>
                </w:pPr>
                …
            </w:p>
            ```
            
            此段落引用了一个 numId 属性为 5 的编号定义实例：
            
            ```xml
            <w:num w:numId="5">
                <w:abstractNumId w:val="4" />
            </w:num>
            ```
            
            numId 属性为 5 的编号定义实例与具有 val 为 5 的编号段落相关联，因此编号段落继承其属性。示例结束】
        
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Num) is located in §A.1. end note]

=== "英文"
    
    This element specifies a unique instance of numbering information that can be referenced by zero or more paragraphs within the parent WordprocessingML document.
    
    This instance requires the referencing of a base abstract numbering definition through the abstractNumId child element ([§17.9.2]). This element also can be used to specify a set of optional overrides applied to zero or more levels from the abstract numbering definition inherited by this instance second though the optional lvlOverride child elements ([§17.9.8]).
    
    [Example: Consider the WordprocessingML for a document with four numbering definition instances, two of which reference the same underlying abstract numbering definition:
    
    ```xml
    <w:numbering>
        …
        <w:num w:numId="2">
            <w:abstractNumId w:val="0" />
        </w:num>
        <w:num w:numId="3">
            <w:abstractNumId w:val="1" />
        </w:num>
        <w:num w:numId="4">
            <w:abstractNumId w:val="4" />
        </w:num>
        <w:num w:numId="5">
            <w:abstractNumId w:val="4" />
        </w:num>
    </w:numbering>
    ```
    
    As shown above, the first two numbering definition instances reference abstractNumId values of 0 and 1 respectively, and the last two both reference the abstract numbering definition with an abstractNumId of 4. end example]
    
    [Example: Consider a numbering definition instance which inherits its information from the abstract numbering definition with abstractNumId of 4, but wishes to use a different set of properties for level 0 of the numbering definition. The resulting WordprocessingML would look like:
    
    ```xml
    <w:num w:numId="6">
        <w:abstractNumId w:val="4" />
        <w:lvlOverride w:ilvl="0">
            <w:lvl w:ilvl="0">
                <w:start w:val="4" />
                <w:lvlText w:val="%1)" />
                <w:lvlJc w:val="start" />
                <w:pPr>
                    <w:ind w:start="360" w:hanging="360" />
                </w:pPr>
            </w:lvl>
        </w:lvlOverride>
    </w:num>
    ```
    
    The lvlOverride element specifies an override for level 0 of the abstract numbering definition. end example]
    
    ??? abstract "Attributes"
    
        **numId** (Numbering Definition Instance ID)
    
        :   Specifies a unique ID which any numbered paragraph which wishes to inherit these numbering properties shall reference using the numPr element ([§17.3.1.19]).
    
            [Example: Consider the WordprocessingML below for an example numbered paragraph:
            
            ```xml
            <w:p>
                <w:pPr>
                    <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                    </w:numPr>
                </w:pPr>
                …
            </w:p>
            ```
            
            This paragraph references a numbering definition instance with a numId attribute of 5:
            
            ```xml
            <w:num w:numId="5">
                <w:abstractNumId w:val="4" />
            </w:num>
            ```
            
            The numbering definition instance with a numId attribute of 5 correlates with the numbered paragraph with the numbering definition instance referent element with a val of 5, so the numbered paragraph inherits its properties. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Num) is located in §A.1. end note]

## 17.9.16 numbering (编号定义)

**numbering (Numbering Definitions)**

=== "中文"
    
    此元素指定了在 WordprocessingML 文档中用于标记单独文本段落的编号格式、显示和功能，包括阿拉伯数字、罗马数字、符号字符（"项目符号"）和文本字符串等。
    
    【示例：以下两个段落都包含由 WordprocessingML 定义的编号：第一个使用阿拉伯数字，第二个使用符号字符：
    
    <ol start=8>
        <li>这是一个具有编号信息的段落。</li>
    <ol>

    <ul>
        <li>这也是一个具有编号信息的段落。</li>
    </ul>
    
    示例结束】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Numbering) is located in §A.1. end note]

=== "英文"
    
    This element specifies the formatting, display, and functionality of numbering - Arabic numerals, Roman numerals, symbol characters ("bullets"), text strings, etc. - in WordprocessingML documents, which are used to label individual paragraphs of text.
    
    [Example: The following two paragraphs each contain numbering as defined by WordprocessingML: the first uses an Arabic numeral, the second a symbol character:
    
    <ol start=8>
        <li>This is a paragraph with numbering information.</li>
    <ol>

    <ul>
        <li>This is also a paragraph with numbering information.</li>
    </ul>
    
    end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Numbering) is located in §A.1. end note]

## 17.9.17 numFmt (编号格式)

**numFmt (Numbering Format)**

=== "中文"
    
    该元素指定了编号定义中此级别的所有编号应使用的编号格式。此信息用于替换级别文本字符串中的 %x，其中 x 是特定的基于一的级别索引，使用适当的值，除非 numFmt 值为 bullet，在这种情况下使用级别文本字符串的字面文本。此值应通过计算自上次使用 val 属性中定义的编号系统以来此级别的段落数来计算。
    
    当文档具有由 format 属性指定的自定义编号格式时，应使用引用的编号格式。如果无法将引用的编号格式解析为编号格式，则使用 val 属性值指定的编号格式。如果 val 属性的相应值为 custom，则结果由实现定义。
    
    如果省略此元素，则假定该级别为十进制级别。
    
    【示例：考虑编号定义中编号级别的以下 WordprocessingML 片段：
    
    ```xml
    <w:lvl w:ilvl="2">
        <w:start w:val="1" />
        <w:numFmt w:val="lowerRoman" />
        <w:lvlRestart w:val="0" />
        <w:lvlText w:val="%3)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="1080" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    ```
    
    numFmt 值为 lowerLetter 表示消费者必须使用小写字母对此级别的所有编号进行编号：a、b、c…… 示例结束】
    
    ??? abstract "Attributes"
    
        **format**（自定义定义的编号格式）
        
        :   使用 XSLT 格式属性定义的语法指定自定义编号格式。
        
            此格式应用于父对象中的所有编号。
            
            【示例：值 &#x30A2; 表示消费者必须使用片假名编号。示例结束】
            
            此属性的可能值由 ST_String 简单类型（[§22.9.2.13]）定义。
        
        **val**（编号格式类型）
        
        :   指定应用于父对象中所有编号的编号格式。
            
            【示例：值 lowerLetter 表示消费者必须对此分组中的每个编号使用小写字母：a、b、c…… 示例结束】
            
            此属性的可能值由 ST_NumberFormat 简单类型（[§17.18.59]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumFmt) is located in §A.1. end note]

=== "英文"
    
    This element specifies the number format that shall be used to display all numbering at this level in the numbering definition. This information is used to replace the level text string %x, where x is a particular one- based level index, with the appropriate value unless the numFmt value is bullet, in which case the literal text of the level text string is used. This value shall be calculated by counting the number of paragraphs at this level since the last restart using the numbering system defined in the val attribute.
    
    When a document has a custom number format specified by the format attribute, it shall use the referenced number format. If the referenced number format cannot be resolved as a number format the consumer shall use the number format specified by the value of the val attribute. If the corresponding value of the val attribute is custom, the result is implementation-defined.
    
    If this element is omitted, the level shall be assumed to be of level type decimal.
    
    [Example: Consider the following WordprocessingML fragment for a numbering level in a numbering definition:
    
    ```xml
    <w:lvl w:ilvl="2">
        <w:start w:val="1" />
        <w:numFmt w:val="lowerRoman" />
        <w:lvlRestart w:val="0" />
        <w:lvlText w:val="%3)" />
        <w:lvlJc w:val="start" />
        <w:pPr>
            <w:ind w:start="1080" w:hanging="360" />
        </w:pPr>
        <w:rPr>
            <w:rFonts w:hint="default" />
        </w:rPr>
    </w:lvl>
    ```
    
    A numFmt value of lowerLetter indicates that a consumer must use lowercase letters for all numbering of this level: a,b,c… end example]
    
    
    ??? abstract "Attributes"
    
        **format** (Custom Defined Number Format)
    
        :   Specifies a custom number format using the syntax defined by the XSLT format attribute.
    
            This format shall be used for all numbering in the parent object.
            
            [Example: A value of &#x30A2; indicates that a consumer must use Katakana numbering. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        **val** (Numbering Format Type)
    
        :   Specifies the number format that shall be used for all numbering in the parent object.
            
            [Example: A value of lowerLetter indicates that a consumer must use lowercase letters for each number in this grouping: a,b,c… end example]
            
            The possible values for this attribute are defined by the ST_NumberFormat simple type ([§17.18.59]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumFmt) is located in §A.1. end note]

## 17.9.18 numId (编号定义实例参考)

**numId (Numbering Definition Instance Reference)**

=== "中文"
    
    该元素指定在 WordprocessingML 文档中给定的父编号段所使用的编号定义实例。
    
    val 属性的值为 0 时，绝不应用于指向编号定义实例，并且只能用于指示样式层次结构中特定级别的编号属性的移除（通常通过直接格式化）。
    
    【示例：考虑下面的 WordprocessingML，其中包含一个示例编号段：
    
    ```xml
    <w:p>
    <w:pPr>
    <w:numPr>
    <w:ilvl w:val="0" />
    <w:numId w:val="5" />
    </w:numPr>
    </w:pPr>
    …
    </w:p>
    ```
    
    该段落引用了一个 numId 属性值为 5 的编号定义实例，如下所示：
    
    ```xml
    <w:num w:numId="5">
    <w:abstractNumId w:val="4" />
    </w:num>
    ```
    
    编号定义实例引用指定了应用于给定段落的给定编号定义实例，该段落本身从 abstractNumId 为 4 的抽象编号定义中继承其属性。示例结束】
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
        
        :   指定该属性的内容包含一个十进制数。
        
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。示例结束]
            
            该属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the numbering definition instance which shall be used for the given parent numbered paragraph in the WordprocessingML document.
    
    A value of 0 for the val attribute shall never be used to point to a numbering definition instance, and shall instead only be used to designate the removal of numbering properties at a particular level in the style hierarchy (typically via direct formatting).
    
    [Example: Consider the WordprocessingML below for an example numbered paragraph:
    
    ```xml
    <w:p>
    <w:pPr>
    <w:numPr>
    <w:ilvl w:val="0" />
    <w:numId w:val="5" />
    </w:numPr>
    </w:pPr>
    …
    </w:p>
    ```
    
    This paragraph references a numbering definition instance with a numId attribute of 5, as follows:
    
    ```xml
    <w:num w:numId="5">
    <w:abstractNumId w:val="4" />
    </w:num>
    ```
    
    The numbering definition instance reference specifies the given numbering definition instance to be applied to the given paragraph, which itself inherits its properties from abstract numbering definition with abstractNumId of 4. end example]
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.19 numIdMacAtCleanup (最后审查的摘要编号定义)

**numIdMacAtCleanup (Last Reviewed Abstract Numbering Definition)**

=== "中文"
    
    这个元素向消费者指示应用程序在尝试从给定文档中删除未使用的抽象编号定义时的进度。如果消费者打开了一个旧版本的文档，它可以选择删除那些“孤立”的抽象编号定义（没有关联的编号定义实例）。这个元素被那些消费者用来指示他们在审查现有的抽象编号定义时的进度（如果尚未完成的话）。【注意：从文档中删除未使用的抽象编号定义可以减小文件大小，但不是必需的。】
    
    如果省略，则所有抽象编号定义都应被视为已审阅。
    
    【示例：考虑一个包含 32 个抽象编号定义的文档，其中 abstractNumId 的值范围从 0 到 85。如果应用程序只在保存时审阅了 abstractNumId 值低于 25 的那些抽象编号定义，它将指示为如下状态：
    
    ```xml
    <w:numIdMacAtCleanup w:val="25"/>
    ```
    
    此值指定所有 abstractNumId 值大于 25 的抽象编号定义尚未被审阅。示例结束】
    
    ??? abstract "属性"
    
        **val**（十进制数值）
    
        :   指定该属性的内容包含一个十进制数。
    
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。示例结束]
            
            该属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
            
            [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies to a consumer the progress in the last attempt made by the application to remove unused abstract numbering definitions from a given document. If a legacy document is opened by a consumer, it can choose to remove abstract numbering definition which are 'orphaned' (have no associated numbering definition instances). This element is used by those consumers to indicate their progress (if not complete) in reviewing existing abstract numbering definitions. [Note: Removing unused abstract numbering definition from a document reduces the file size, but is not required. end note]
    
    If omitted, then all abstract numbering definitions shall be considered reviewed.
    
    [Example: Consider a document with 32 abstract numbering definitions, with abstractNumId values ranging from 0 to 85. If an application has only reviewed those abstract numbering definitions with abstractNumId values lower than 25 at save time, it would indicate that state as follows:
    
    ```xml
    <w:numIdMacAtCleanup w:val="25"/>
    ```
    
    This value specifies that all abstract numbering definitions with an abstractNumId value higher than 25 have not yet been reviewed. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
            
            [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.20 numPicBullet (图片编号符号定义)

**numPicBullet (Picture Numbering Symbol Definition)**

=== "中文"
    
    这个元素指定了文档中编号级别定义中要使用的特定图片的外观和行为，并且是 WordprocessingML 文档中所有图片编号符号信息的基础。
    
    这个元素不直接在抽象编号定义中使用，而是通过其 numPicBulletId 属性被编号级别定义中使用的 lvlPicBulletId 元素（[§17.9.9]）引用。
    
    【示例：考虑下面的 WordprocessingML 片段，说明了如何通过 numPicBulletId 属性引用 numPicBullet 定义的图片编号符号定义：
    
    ```xml
    <w:numPicBullet w:numPicBulletId="1">
        <w:drawing>
        …
        </w:drawing>
    </w:numPicBullet>
    …
    <w:abstractNum w:abstractNumId="7">
        <w:nsid w:val="71A06359" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:tmpl w:val="10643FE6" />
        <w:lvl w:ilvl="0" w:tplc="B7663E56">
            <w:start w:val="1" />
            <w:numFmt w:val="bullet" />
            <w:lvlText w:val=" " />
            <w:lvlPicBulletId w:val="1" />
        </w:lvl>
    </w:abstractNum>
    ```
    
    lvlPicBulletId 元素引用了一个 numPicBullet 元素，该元素定义了文档中此类型图片符号的大小和外观。需要注意的是，这个图片符号可以被多个不同编号定义中的多个级别引用。示例结束】
    
    ??? abstract "Attributes"
    
        **numPicBulletId**（图片编号符号 ID）
        
        :   指定此图片符号定义的唯一 ID，用于从编号级别定义中引用此图片符号。
            
            【示例：考虑下面的 WordprocessingML 片段，说明了如何通过 numPicBulletId 属性引用 numPicBullet 定义的图片编号符号定义：
            
            ```xml
            <w:numPicBullet w:numPicBulletId="1">
                …
            </w:numPicBullet>
            …
            <w:abstractNum w:abstractNumId="7">
                <w:lvl w:ilvl="0" w:tplc="B7663E56">
                    …
                    <w:lvlPicBulletId w:val="1" />
                </w:lvl>
            </w:abstractNum>
            ```
            
            lvlPicBulletId 元素直接引用了 numPicBulletId 属性中的 ID。示例结束】
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumPicBullet) is located in §A.1. end note]

=== "英文"
    
    This element specifies the appearance and behavior of a specific picture to be used as the numbering symbol within a numbering level definition in a document, and is the basis for all picture numbering symbol information in a WordprocessingML document.
    
    This element is not used directly within abstract numbering definitions but rather is referenced through its numPicBulletId attribute by the lvlPicBulletId element ([§17.9.9]) used within numbering level definitions.
    
    [Example: Consider the WordprocessingML fragment below which illustrates how a numPicBullet definition is referenced by a picture numbering symbol definition reference through its numPicBulletId attribute:
    
    ```xml
    <w:numPicBullet w:numPicBulletId="1">
        <w:drawing>
        …
        </w:drawing>
    </w:numPicBullet>
    …
    <w:abstractNum w:abstractNumId="7">
        <w:nsid w:val="71A06359" />
        <w:multiLevelType w:val="hybridMultilevel" />
        <w:tmpl w:val="10643FE6" />
        <w:lvl w:ilvl="0" w:tplc="B7663E56">
            <w:start w:val="1" />
            <w:numFmt w:val="bullet" />
            <w:lvlText w:val=" " />
            <w:lvlPicBulletId w:val="1" />
        </w:lvl>
    </w:abstractNum>
    ```
    
    The lvlPicBulletId element references a numPicBullet element, which defines the size and appearance of all picture bullets of this picture bullet type within the document. It is important to note that this picture bullet can be referenced by multiple levels of various numbering definitions. end example]
    
    ??? abstract "Attributes"
    
        **numPicBulletId** (Picture Numbering Symbol ID)
    
        :   Specifies a unique ID for this picture bullet definition which shall be used to reference this picture bullet from a numbering level definition.
    
            [Example: Consider the WordprocessingML fragment below which illustrates how a numPicBullet definition is referenced by a picture numbering symbol definition reference through its numPicBulletId attribute:
            
            ```xml
            <w:numPicBullet w:numPicBulletId="1">
                …
            </w:numPicBullet>
            …
            <w:abstractNum w:abstractNumId="7">
                <w:lvl w:ilvl="0" w:tplc="B7663E56">
                    …
                    <w:lvlPicBulletId w:val="1" />
                </w:lvl>
            </w:abstractNum>
            ```
            
            The lvlPicBulletId element references the ID in the numPicBulletId attribute directly. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NumPicBullet) is located in §A.1. end note]


## 17.9.21 numStyleLink (编号样式参考)

**numStyleLink (Numbering Style Reference)**

=== "中文"
    
    这个元素指定一个抽象编号，不包含其编号类型的实际编号属性，而是作为对存储在文档中的编号样式的引用，当引用此抽象编号定义时应用该编号样式，并且它本身指向要使用的实际底层抽象编号定义。
    
    当引用此抽象编号定义时要应用的编号样式由 numStyleLink 的 val 属性中包含的字符串标识。
    
    【示例：考虑以下抽象编号定义：
    
    ```xml
    <w:abstractNum w:abstractNumId="0">
        <w:nsid w:val="38901FA4" />
        <w:multiLevelType w:val="multilevel" />
        <w:numStyleLink w:val="TestNumberingStyle" />
    </w:abstractNum>
    ```
    
    这个抽象编号定义引用了具有 styleId 属性等于 TestNumberingStyle 的编号样式，如下所示：
    
    ```xml
    <w:style w:type="numbering" w:styleId="TestNumberingStyle">
        …
    </w:style>
    ```
    
    因此，每当基本抽象编号定义被编号段继承时，必须应用此编号样式。示例结束】
    
    
    ??? abstract "Attributes"
    
        **val**（字符串值）
        
        :   指定其内容包含一个字符串。
        
            该字符串的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是相关段落样式的 styleId。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近的祖先结构化文档标记的标题。在每种情况下，值都是在父元素的上下文中解释的。示例结束】

            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).

    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies an abstract numbering that does not contain the actual numbering properties for its numbering type, but rather serves as a reference to a numbering style stored in the document, which shall be applied when this abstract numbering definition is referenced, and itself points at the actual underlying abstract numbering definition to be used.
    
    The numbering style that is to be applied when this abstract numbering definition is referenced is identified by the string contained in numStyleLink's val attribute.
    
    [Example: Consider the abstract numbering definition below:
    
    ```xml
    <w:abstractNum w:abstractNumId="0">
        <w:nsid w:val="38901FA4" />
        <w:multiLevelType w:val="multilevel" />
        <w:numStyleLink w:val="TestNumberingStyle" />
    </w:abstractNum>
    ```
    
    This abstract numbering definition references the numbering style with a styleId attribute equal to TestNumberingStyle, as follows below:
    
    ```xml
    <w:style w:type="numbering" w:styleId="TestNumberingStyle">
        …
    </w:style>
    ```
    
    Therefore, this numbering style must be applied whenever the base abstract numbering definition is inherited by a numbered paragraph. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
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


## 17.9.22 pPr (编号级别关联段落的属性)

**pPr (Numbering Level Associated Paragraph Properties)**

=== "中文"
    
    这个元素指定了在父编号定义中的特定编号级别中应用的段落属性。这些段落属性应用于引用给定编号定义和编号级别的任何带编号的段落。
    
    在带编号的段落本身上指定的段落属性会覆盖编号级别元素内的 pPr 元素指定的段落属性（[§17.9.5]，[§17.9.6]）。
    
    【示例：考虑以下 WordprocessingML，指定了编号级别段落属性：
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            …
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    ```
    
    pPr 元素内指定的每个段落属性都应用于继承此编号级别定义作为编号属性的任何带编号的段落，按照样式层次结构中定义的顺序应用。示例结束】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_PPrGeneral) is located in §A.1. end note]

=== "英文"
    
    This element specifies the paragraph properties which shall be applied as part of a given numbering level within the parent numbering definition. These paragraph properties are applied to any numbered paragraph that references the given numbering definition and numbering level.
    
    Paragraph properties specified on the numbered paragraph itself override the paragraph properties specified by pPr elements within a numbering lvl element ([§17.9.5], [§17.9.6]).
    
    [Example: Consider the WordprocessingML below which specifies numbering level paragraph properties:
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            …
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
        </w:lvl>
    </w:abstractNum>
    ```
    
    Each of the paragraph properties specified inside the pPr element are applied to any numbered paragraph which inherits this numbering level definition as part of the numbering properties in the order defined by the style hierarchy. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_PPrGeneral) is located in §A.1. end note]

## 17.9.23 pStyle (段落样式关联的编号级别)

**pStyle (Paragraph Style's Associated Numbering Level)**

=== "中文"
    
    这个元素指定了一个段落样式的名称，当应用到文档内容时，该样式将自动应用该编号级别。当定义一个段落样式以包含一个编号定义时，任何由 numPr 元素（[§17.3.1.19]）定义的编号级别都将被忽略，而代之以此元素指定的与该段落样式相关联的编号级别。
    
    如果这个元素引用了一个不存在或不是段落样式的样式，则可以忽略它。
    
    【示例：考虑以下 WordprocessingML，指定了当应用到文档中的段落时，样式为 example 的段落样式也必须应用抽象编号定义的第一个编号级别，该编号定义的 abstractNumId 等于 1，如下所示：
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            …
            <w:pStyle w:val="example" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
            …
        </w:lvl>
    </w:abstractNum>
    ```
    
    段落样式的样式定义只包括编号定义实例的 numId，而不包括它的级别：
    
    ```xml
    <w:style w:styleId="example" w:type="paragraph">
        …
        <w:pPr>
            <w:numPr>
            <w:numId w:val="0" />
            </w:numPr>
        </w:pPr>
    </w:style>
    ```
    
    示例结束】
    
    
    ??? abstract "Attributes"
    
        **val**（字符串值）
        
        :   指定其内容包含一个字符串。
        
            该字符串的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
            
            但是，请考虑以下片段：
            
            ```xml
            <w:sdtPr>
            <w:alias w:val="SDT Title Example" />
            …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近的祖先结构化文档标记的标题。在每种情况下，该值是根据父元素的上下文进行解释的。示例结束】
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the name of a paragraph style which shall automatically this numbering level when applied to the contents of the document. When a paragraph style is defined to include a numbering definition, any numbering level defined by the numPr element ([§17.3.1.19]) shall be ignored, and instead this element shall specify the numbering level associated with that paragraph style.
    
    If this element references a style which does not exist, or is not a paragraph style, then it can be ignored. [Example: Consider the WordprocessingML below which specifies that the paragraph style with styleId example, when applied to paragraphs in the document, must also apply the first numbering level of the abstract numbering definition with an abstractNumId equal to 1, as follows:
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            …
            <w:pStyle w:val="example" />
            <w:pPr>
                <w:tabs>
                    <w:tab w:val="num" w:pos="720" />
                </w:tabs>
                <w:ind w:start="720" w:hanging="360" />
            </w:pPr>
            …
        </w:lvl>
    </w:abstractNum>
    ```
    
    The style definition for the paragraph style would only include the numId of the numbering definition instance, and not its level:
    
    ```xml
    <w:style w:styleId="example" w:type="paragraph">
        …
        <w:pPr>
            <w:numPr>
            <w:numId w:val="0" />
            </w:numPr>
        </w:pPr>
    </w:style>
    ```
    
    end example]
    
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
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

## 17.9.24 rPr (编号符号的运行(Run)属性)

**rPr (Numbering Symbol Run Properties)**

=== "中文"
    
    该元素指定应用于文档中的段落的编号级别文本（由 lvlText 元素指定）的运行属性。
    
    这些运行属性应用于给定抽象编号定义和编号级别使用的所有编号级别文本。应该注意，指定在编号段落本身或编号段落中的文本运行上的运行属性与编号级别中的 rPr 元素指定的运行属性是分开的，因为后者仅影响编号文本本身，而不影响编号段落中的其他运行。
    
    【示例：考虑以下 WordprocessingML，其中使用 rPr 元素指定给定编号级别内使用的编号符号应为粗体，并且字号为 16：
    
    ```xml
    <w:lvl w:ilvl="1">
        …
        <w:rPr>
            <w:b />
            <w:sz w:val="32" />
        </w:rPr>
    </w:lvl>
    ```
    
    生成的段落使用其常规段落格式，但编号级别文本本身必须特别以粗体格式和 16 号字体显示。示例结束】
    
    该元素的内容模型（CT_RPr）的 W3C XML Schema 定义位于 §A.1。以上表中的每个子元素不得出现超过一次。【注：由于 W3C XML Schema 语言的限制，该限制未反映在元素的内容模型中。】

=== "英文"
    
    This element specifies the run properties which shall be applied to the numbering level's text specified in the lvlText element ([§17.9.11]) when it is applied to paragraphs in this document.
    
    These run properties are applied to all numbering level text used by a given abstract numbering definition and numbering level. It should be noted that run properties specified on a numbered paragraph itself, or on text runs within a numbered paragraph, are separate from the run properties specified by rPr elements within a numbering level, as the latter affects only the numbering text itself, not the remainder of runs in the numbered paragraph.
    
    [Example: Consider the WordprocessingML below which uses the rPr element to specify that the numbering symbol used within a given  umbering level should be bold and of a 16 point font size:
    
    ```xml
    <w:lvl w:ilvl="1">
        …
        <w:rPr>
            <w:b />
            <w:sz w:val="32" />
        </w:rPr>
    </w:lvl>
    ```
    
    The resulting paragraph uses its regular paragraph formatting, but the numbering level text itself must be specifically formatted as bold in 16 point font. end example]
    
    The W3C XML Schema definition of this element’s content model (CT_RPr) is located in §A.1. Each child element from the above table shall not occur more than once. [Note: This restriction is not reflected in the element's content model due to limitations of W3C XML Schema language. end note]

## 17.9.25 start (起始值)

**start (Starting Value)**

=== "中文"
    
    该元素指定父编号级别在给定编号级别定义中使用的编号的起始值。当此级别在文档中首次启动时，以及每当通过 lvlRestart 元素（[§17.9.10]）中设置的属性重新启动时，将使用此值。
    
    如果省略此元素，则起始值应为零（0）。
    
    【示例：考虑以下用于抽象编号定义的 WordprocessingML 片段：
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            <w:start w:val="2" />
            <w:numFmt w:val="upperLetter"/>
            …
        </w:lvl>
    </w:abstractNum>
    ```
    
    在此示例中，由于使用大写西方字母（upperLetter）作为此编号级别的编号符号，因此与此抽象编号定义和编号级别关联的编号段落的第一个实例将具有编号符号 B，即数字格式中的第二个字母。
    
    具有此抽象编号定义且在此级别的后续编号段落将从 B（此编号级别的起始值）开始递增其编号符号。示例结束】
    
    
    ??? abstract "Attributes"
            
        **val**（十进制数值）
    
        :   指定此属性的内容包含十进制数。
        
            此十进制数的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下简单类型 ST_DecimalNumber 的数值 WordprocessingML 属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val 属性的值是一个十进制数，其值必须在父元素的上下文中进行解释。示例结束】
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the starting value for the numbering used by the parent numbering level within a given numbering level definition. This value is used when this level initially starts in a document, as well as whenever it is restarted via the properties set in the lvlRestart element ([§17.9.10]).
    
    If this element is omitted, then the starting value shall be zero (0).
    
    [Example: Consider the following WordprocessingML fragment for an abstract numbering definition:
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:lvl w:ilvl="0">
            <w:start w:val="2" />
            <w:numFmt w:val="upperLetter"/>
            …
        </w:lvl>
    </w:abstractNum>
    ```
    
    In this example, since upper case Western letters (upperLetter) are being used as numbering symbols for this numbering level, the first instance of a numbering paragraph associated with this abstract numbering definition and numbering level would have the numbering symbol B, the second letter in the number format.
    
    Subsequent numbered paragraphs with this abstract numbering definition and at this level would have their numbering symbols incremented from B (the starting value for this numbering level). end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.26 startOverride (编号级别起始值覆盖)

**startOverride (Numbering Level Starting Value Override)**

=== "中文"
    
    这个元素指定了指定级别覆盖的编号从哪里开始。这个值用于在给定级别重置编号。
    
    【示例：考虑使用 WordprocessingML 来覆盖特定列表项的编号，并使列表如下所示：
    
    首先，创建两个 w:num 实例，它们引用相同的抽象编号定义。其中一个 w:num 实例覆盖了第一级的编号值。下面是说明这一点的 Wordprocessing ML：
    
    ![123](./imgs/Image9497.png)
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4"/>
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4"/>
        <w:lvlOverride w:ilvl="0">
            <w:startOverride w:val = "1"/>
        </w:lvlOverride>
    </w:num>
    ```
    
    然后，在主文档中，使用 numId 5 对第一和第二段落进行编号为“1”和“2”，并使用 numId 6 将第三段落的编号重置为“1”。接着，第四段落的编号变为“2”，因为它是基于新的重置值递增的。下面是说明这一点的 WordprocessingML：】
    
    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 1</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 2</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="6" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 3</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 4</w:t>
        </w:r>
    </w:p>
    ```
    
    end example]
    
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
        
        :   指定此属性的内容包含一个十进制数。
        
            此十进制数的内容根据父 XML 元素的上下文进行解释。
        
            [示例：考虑以下简单类型 ST_DecimalNumber 的数字 WordprocessingML 属性：
        
            ```xml
            <… w:val="1512645511" />
            ```
        
            val 属性的值是一个十进制数，其值必须在父元素的上下文中进行解释。示例结束]
        
            此属性的可能值由 ST_DecimalNumber 简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the number that the specified level override shall begin with. This value is used to reset the numbering in a given level.
    
    [Example: Consider using WordprocessingML to override the numbering of a particular list item and make the list look as follows:
    
    Firstly, create two w:num instances that reference the same abstract numbering definition. One of the w:num instance overrides the numbering value for the first level. Below is the Wordprocessing ML that illustrates this:
    
    ![123](./imgs/Image9497.png)
    
    ```xml
    <w:num w:numId="5">
        <w:abstractNumId w:val="4"/>
    </w:num>
    <w:num w:numId="6">
        <w:abstractNumId w:val="4"/>
        <w:lvlOverride w:ilvl="0">
            <w:startOverride w:val = "1"/>
        </w:lvlOverride>
    </w:num>
    ```
    
    Then, in the main document, number the first and the second paragraph as “1” and “2” respectively by using numId 5, and reset the numbering of the third paragraph to “1” by using numId 6. In turn, the numbering of the fourth paragraph becomes "2", because it is incremented based on the new reset value. Below is the WordprocessingML that illustrates this:
    
    ```xml
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 1</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 2</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="6" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 3</w:t>
        </w:r>
    </w:p>
    <w:p>
        <w:pPr>
            <w:numPr>
                <w:ilvl w:val="0" />
                <w:numId w:val="5" />
            </w:numPr>
        </w:pPr>
        <w:r>
            <w:t>Line 4</w:t>
        </w:r>
    </w:p>
    ```
    
    end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
    
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

## 17.9.27 styleLink (编号样式定义)

**styleLink (Numbering Style Definition)**

=== "中文"

    这个元素指定了父抽象编号定义是指定编号样式的基本编号定义，其在其 val 属性中引用。
    
    如果省略此元素，或者它引用不存在的样式，则此编号定义将不是编号样式的基本属性。
    
    【注：编号样式从不直接由文档中的段落或文本运行引用 - 相反，抽象编号定义指定它包含编号样式的基本编号信息，并且一个或多个编号定义实例引用从中继承的编号定义。编号样式本身只是抽象编号定义上的友好名称。 结束注释】
    
    【示例：考虑下面的 WordprocessingML 片段，表示一个抽象编号定义，它定义了编号样式的属性：
    
    ```xml
    <w:numbering>
        …
        <w:abstractNum w:abstractNumId="5">
            …
            <w:styleLink w:val="ExampleNumberingStyle" />
            …
        </w:abstractNum>
    </w:numbering>
    …
    <w:styles>
        …
        <w:style w:type="numbering" w:styleId="ExampleNumberingStyle">
            <w:name w:val="ExampleNumberingStyle" />
            …
            <w:pPr>
                <w:numPr>
                    <w:numId w:val="6" />
                </w:numPr>
            </w:pPr>
        </w:style>
        …
    </w:styles>
    ```
    
    styleLink 元素指定抽象编号定义定义了样式 ID 与其 val 属性匹配的编号样式的属性，并在 WordprocessingML 的 styles 元素中定义。】
    
    end example]
    
    
    ??? abstract "Attributes"
    
        **val**（字符串值）
        
        :   指定其内容包含一个字符串。
        
            该字符串的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId。
            
            但是，请考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近的祖先结构化文档标记的标题。 在每种情况下，值都是在父元素的上下文中解释的。】
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"

    
    This element specifies that the parent abstract numbering definition is the base numbering definition for the specified numbering style referenced in its val attribute.
    
    If this element is omitted, or it references a style which does not exist, then this numbering definition shall not be the underlying properties for a numbering style.
    
    [Note: Numbering styles are never directly referenced by paragraphs or runs in the document – instead, an abstract numbering definition specifies that it contains the underlying numbering information for a numbering style, and one or more numbering definition instances reference a numbering definition which inherits from it. The numbering style itself is just a friendly name on an abstract numbering definition. end note]
    
    [Example: Consider the WordprocessingML fragment below, representing an abstract numbering definition which defines the properties for a numbering style:
    
    ```xml
    <w:numbering>
        …
        <w:abstractNum w:abstractNumId="5">
            …
            <w:styleLink w:val="ExampleNumberingStyle" />
            …
        </w:abstractNum>
    </w:numbering>
    …
    <w:styles>
        …
        <w:style w:type="numbering" w:styleId="ExampleNumberingStyle">
            <w:name w:val="ExampleNumberingStyle" />
            …
            <w:pPr>
                <w:numPr>
                    <w:numId w:val="6" />
                </w:numPr>
            </w:pPr>
        </w:style>
        …
    </w:styles>
    ```
    
    The styleLink element specifies that the abstract numbering definition defines the properties for a numbering style whose styleId matches its val attribute, and is defined in the styles element of the WordprocessingML.
    
    end example]
    
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
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

## 17.9.28 suff (编号符号和段落文本之间的内容)

**suff (Content Between Numbering Symbol and Paragraph Text)**

=== "中文"
    
    这个元素指定了在给定编号级别的文本和引用该编号级别的每个编号段落的文本之间应添加的内容。
    
    如果省略此元素，则其值将被假定为制表符。
    
    【示例：考虑以下编号段落：
    
    ![123](./imgs/Image9511.png)
    
    在此示例中，编号符号1.和编号段落文本“Test”之间存在一个空格。空格将在WordprocessingML中指定如下：
    
    ```xml
    <w:lvl w:ilvl="0">
        …
        <w:suff w:val="space" />
        …
    </w:lvl>
    ```
    
    具有值为space的suff元素指定编号级别文本和段落文本之间的字符必须是一个空格。示例结束】
    
    ??? abstract "属性"
    
        **val**（编号和文本之间的字符类型）
        
        :   指定应跟在列表编号后面的字符。
        
            【示例：考虑一个编号段落，编号符号和编号段落的文本之间存在一个制表符。该制表符将在WordprocessingML中指定如下：
            
            ```xml
            <w:lvl w:ilvl="0">
                …
                <w:suff w:val="tab" />
                …
            </w:lvl>
            ```
            
            值为tab的val属性指定编号级别文本和段落文本之间的字符必须是一个制表符。此制表符遵循正常的制表位规则。示例结束】
            
            The possible values for this attribute are defined by the ST_LevelSuffix simple type ([§17.18.46]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LevelSuffix) is located in §A.1. end note]

=== "英文"
    
    This element specifies the content which shall be added between a given numbering level's text and the text of every numbered paragraph which references that numbering level.
    
    If this element is omitted, then its value shall be assumed to be tab.
    
    [Example: Consider the numbered paragraph below:
    
    ![123](./imgs/Image9511.png)
    
    In this example, a space exists between the numbering symbol 1. and the numbered paragraph text Test. The space would be specified in WordprocessingML as follows:
    
    ```xml
    <w:lvl w:ilvl="0">
        …
        <w:suff w:val="space" />
        …
    </w:lvl>
    ```
    
    The suff element with an attribute value of space specifies that the character between the numbering's level text and the paragraph text must be a space. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Character Type Between Numbering and Text)
    
        :   Specifies the character which shall follow the list number.
    
            [Example: Consider a numbered for which a tab exists between the numbering symbol and the numbered paragraph's text. The tab would be specified in WordprocessingML as follows:
            
            ```xml
            <w:lvl w:ilvl="0">
                …
                <w:suff w:val="tab" />
                …
            </w:lvl>
            ```
            
            The val attribute with a value of tab specifies that the character between the numbering's level text and the paragraph text must be a tab. This tab follows normal tab stop rules. end example]
            
            The possible values for this attribute are defined by the ST_LevelSuffix simple type ([§17.18.46]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LevelSuffix) is located in §A.1. end note]

## 17.9.29 tmpl (编号模板代码)

**tmpl (Numbering Template Code)**

=== "中文"

    这个元素指定了一个唯一的十六进制代码，用于确定此抽象编号定义应该显示在应用程序用户界面中的位置。
    
    如果省略此元素，则此抽象编号定义可以显示在消费者选择的任何位置。
    
    【示例：考虑以下抽象编号定义：
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:tmpl w:val="CA48B6BA" />
        …
    </w:abstractNum>
    ```
    
    在这个示例中，具有属性abstractNumId等于1的abstractNum元素将显示在消费者应用程序用户界面中的模板代码CA48B6BA指定的区域内。示例结束】
    
    ??? abstract "属性"
    
        **val**（长十六进制数字值）
        
        :   指定一个数值（以四位十六进制数字表示），其内容根据父XML元素的上下文进行解释。
        
            【示例：考虑简单类型ST_LongHexNumber属性的以下值：00BE2C6C。
            
            这个值是允许的，因为它包含四个十六进制数字，每个数字都是实际十进制数字值的一个字节的编码。因此，它可以根据父XML元素的上下文进行解释。示例结束】
            
            此属性的可能值由ST_LongHexNumber简单类型定义（[§17.18.50]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LongHexNumber) is located in §A.1. end note]

=== "英文"

    This element specifies a unique hexadecimal code which can be used to determine a location within application user interface in which this abstract numbering definition shall be displayed.
    
    If this element is omitted, then this abstract numbering definition can be displayed in any location chosen by the consumer.
    
    [Example: Consider the following abstract numbering definition:
    
    ```xml
    <w:abstractNum w:abstractNumId="1">
        …
        <w:tmpl w:val="CA48B6BA" />
        …
    </w:abstractNum>
    ```
    
    In this example the abstractNum element with attribute abstractNumId equal to 1, would appear in the area within a consumer's application user interface specified by the template code CA48B6BA.end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Long Hexadecimal Number Value)
    
        :   Specifies a number value specified as a four digit hexadecimal number), whose contents of this decimal number are interpreted based on the context of the parent XML element.
    
            [Example: Consider the following value for an attribute of simple type ST_LongHexNumber: 00BE2C6C.
            
            This value is permitted, as it contains four hexadecimal digits, each an encoding of an octet of the actual decimal number value. It can therefore be interpreted as desired in the context of the parent XML element, end example]
            
            The possible values for this attribute are defined by the ST_LongHexNumber simple type ([§17.18.50]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_LongHexNumber) is located in §A.1. end note]

[§17.9.1]: #1791-abstractnum-摘要编号定义
[§17.9.2]: #1792-abstractnumid-摘要编号定义参考
[§17.9.3]: #1793-ilvl-编号级别参考
[§17.9.4]: #1794-islgl-使用阿拉伯数字显示所有级别
[§17.9.5]: #1795-lvl-编号级别覆盖定义
[§17.9.6]: #1796-lvl-编号级别定义
[§17.9.7]: #1797-lvljc-理由
[§17.9.8]: #1798-lvloverride-编号级别定义覆盖
[§17.9.9]: #1799-lvlpicbulletid-图片编号符号定义参考
[§17.9.10]: #17910-lvlrestart-重新启动编号级别符号
[§17.9.11]: #17911-lvltext-编号级别文本
[§17.9.12]: #17912-multileveltype-抽象编号定义类型
[§17.9.13]: #17913-name-摘要编号定义名称
[§17.9.14]: #17914-nsid-抽象编号定义标识符
[§17.9.15]: #17915-num-编号定义实例
[§17.9.16]: #17916-numbering-编号定义
[§17.9.17]: #17917-numfmt-编号格式
[§17.9.18]: #17918-numid-编号定义实例参考
[§17.9.19]: #17919-numidmacatcleanup-最后审查的摘要编号定义
[§17.9.20]: #17920-numpicbullet-图片编号符号定义
[§17.9.21]: #17921-numstylelink-编号样式参考
[§17.9.22]: #17922-ppr-编号级别关联段落的属性
[§17.9.23]: #17923-pstyle-段落样式关联的编号级别
[§17.9.24]: #17924-rpr-编号符号的运行run属性
[§17.9.25]: #17925-start-起始值
[§17.9.26]: #17926-startoverride-编号级别起始值覆盖
[§17.9.27]: #17927-stylelink-编号样式定义
[§17.9.28]: #17928-suff-编号符号和段落文本之间的内容
[§17.9.29]: #17929-tmpl-编号模板代码


[§17.3.1.19]: ./03paragraphs.md#173119-numpr-编号定义实例参考

[§17.17.4]: ./17miscellaneous.md#17174-布尔属性-ct_onoff

[§17.18.2]: ./18simpletypes.md#17182-st_border-边框样式
[§17.18.3]: ./18simpletypes.md#17183-st_brclear-换行文本换行重新开始位置
[§17.18.4]: ./18simpletypes.md#17184-st_brtype-break-类型
[§17.18.5]: ./18simpletypes.md#17185-st_captionpos-自动字幕定位值
[§17.18.6]: ./18simpletypes.md#17186-st_chaptersep-章节分隔符类型
[§17.18.7]: ./18simpletypes.md#17187-st_characterspacing-字符级空白压缩设置
[§17.18.8]: ./18simpletypes.md#17188-st_combinebrackets-两行合一封闭字符类型
[§17.18.10]: ./18simpletypes.md#171810-st_decimalnumber-十进制数值
[§17.18.12]: ./18simpletypes.md#171812-st_direction-双向方向类型
[§17.18.14]: ./18simpletypes.md#171814-st_docgrid-文档网格类型
[§17.18.20]: ./18simpletypes.md#171820-st_dropcap-文本框架首字下沉位置
[§17.18.23]: ./18simpletypes.md#171823-st_eighthpointmeasure-以八分之一点为单位的测量
[§17.18.24]: ./18simpletypes.md#171824-st_em-强调标记类型
[§17.18.35]: ./18simpletypes.md#171835-st_hanchor-水平锚点位置
[§17.18.37]: ./18simpletypes.md#171837-st_heightrule-高度规则
[§17.18.38]: ./18simpletypes.md#171838-st_hexcolor-色值
[§17.18.40]: ./18simpletypes.md#171840-st_highlightcolor-文本突出显示颜色
[§17.18.41]: ./18simpletypes.md#171841-st_hint-字体类型提示
[§17.18.42]: ./18simpletypes.md#171842-st_hpsmeasure-以半点测量
[§17.18.44]: ./18simpletypes.md#171844-st_jc-水平对齐类型
[§17.18.46]: ./18simpletypes.md#171846-st_levelsuffix-编号符号和段落文本之间的内容
[§17.18.47]: ./18simpletypes.md#171847-st_linenumberrestart-行编号重新启动位置
[§17.18.48]: ./18simpletypes.md#171848-st_linespacingrule-行距规则
[§17.18.50]: ./18simpletypes.md#171850-st_longhexnumber-八位十六进制值
[§17.18.59]: ./18simpletypes.md#171859-st_numberformat-编号格式
[§17.18.60]: ./18simpletypes.md#171860-st_objectdrawaspect-嵌入对象表示
[§17.18.61]: ./18simpletypes.md#171861-st_objectupdatemode-嵌入对象更新模式
[§17.18.62]: ./18simpletypes.md#171862-st_pageborderdisplay-页面边框显示选项
[§17.18.63]: ./18simpletypes.md#171863-st_pageborderoffset-页面边框定位底座
[§17.18.64]: ./18simpletypes.md#171864-st_pageborderzorder-页面边框-z-顺序
[§17.18.65]: ./18simpletypes.md#171865-st_pageorientation-页面方向
[§17.18.68]: ./18simpletypes.md#171868-st_pointmeasure-以点为单位的测量
[§17.18.71]: ./18simpletypes.md#171871-st_ptabalignment-绝对位置标签对齐
[§17.18.72]: ./18simpletypes.md#171872-st_ptableader-绝对位置制表符引导符
[§17.18.73]: ./18simpletypes.md#171873-st_ptabrelativeto-绝对位置-标签定位底座
[§17.18.74]: ./18simpletypes.md#171874-st_restartnumber-脚注尾注编号重新开始位置
[§17.18.75]: ./18simpletypes.md#171875-st_rubyalign-拼音指南文本对齐
[§17.18.76]: ./18simpletypes.md#171876-st_sdtdatemappingtype-日期存储格式类型
[§17.18.77]: ./18simpletypes.md#171877-st_sectionmark-节类型
[§17.18.78]: ./18simpletypes.md#171878-st_shd-底纹图案
[§17.18.79]: ./18simpletypes.md#171879-st_shorthexnumber-四位十六进制值
[§17.18.80]: ./18simpletypes.md#171880-st_signedhpsmeasure-以半点为单位的带符号测量
[§17.18.81]: ./18simpletypes.md#171881-st_signedtwipsmeasure-以二十分之一为单位的有符号测量
[§17.18.82]: ./18simpletypes.md#171882-st_stylesort-样式排序设置
[§17.18.83]: ./18simpletypes.md#171883-st_styletype-样式类型
[§17.18.86]: ./18simpletypes.md#171886-st_targetscreensz-生成网页的目标屏幕尺寸
[§17.18.89]: ./18simpletypes.md#171889-st_tblstyleoverridetype-条件表样式格式设置类型
[§17.18.91]: ./18simpletypes.md#171891-st_textalignment-垂直文本对齐类型
[§17.18.92]: ./18simpletypes.md#171892-st_textboxtightwrap-文本框内的行紧密环绕
[§17.18.93]: ./18simpletypes.md#171893-st_textdirection-文本流方向
[§17.18.94]: ./18simpletypes.md#171894-st_texteffect-动画文字效果
[§17.18.95]: ./18simpletypes.md#171895-st_textscale-文本扩展压缩百分比
[§17.18.96]: ./18simpletypes.md#171896-st_theme-主题字体
[§17.18.97]: ./18simpletypes.md#171897-st_themecolor-主题颜色
[§17.18.98]: ./18simpletypes.md#171898-st_ucharhexnumber-两位十六进制值
[§17.18.99]: ./18simpletypes.md#171899-st_underline-下划线图案
[§17.18.100]: ./18simpletypes.md#1718100-st_vanchor-垂直锚点位置
[§17.18.101]: ./18simpletypes.md#1718101-st_verticaljc-垂直排列型
[§17.18.102]: ./18simpletypes.md#1718102-st_view-文档视图值
[§17.18.103]: ./18simpletypes.md#1718103-st_wmlcolorschemeindex-主题颜色参考
[§17.18.104]: ./18simpletypes.md#1718104-st_wrap-文本环绕文本框架类型


[§22.9.2.4]: ../chapter22/sharedsimpletypes.md#22924-st_guid-128-bit-guid
[§22.9.2.6]: ../chapter22/sharedsimpletypes.md#22926-st_lang-语言参考
[§22.9.2.7]: ../chapter22/sharedsimpletypes.md#22927-st_onoff-开关值
[§22.9.2.13]: ../chapter22/sharedsimpletypes.md#229213-st_string-字符串
[§22.9.2.14]: ../chapter22/sharedsimpletypes.md#229214-st_twipsmeasure-以二十分之一点为单位的测量
[§22.9.2.18]: ../chapter22/sharedsimpletypes.md#229218-st_xalign-水平对齐位置
[§22.9.2.20]: ../chapter22/sharedsimpletypes.md#229220-st_yalign-垂直对齐位置