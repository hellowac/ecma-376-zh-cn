# Annex E. (informative) WordprocessingML 自定义 XML 数据提取

**WordprocessingML Custom XML Data Extraction**

=== "中文"

    在[§17.5]中描述的自定义XML标记功能允许WordprocessingML文档包含超出ECMA-376指定的自定义XML语义。为了从WordprocessingML内容中提取这些语义，应用程序可以使用任何所需的方法。
    
    例如，下面包含了一个执行此任务的XSL转换，当应用于主文档部分时，将提取任何自定义XML标记。
    
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns:w="http://purl.oclc.org/ooxml/wordprocessingml/main">
    
        <!-- 此参数应与ignoreMixedContent设置具有相同的值（见第1部分的17.15.1.54） -->
        <xsl:param name="ignoreMixedContent" select="false()"/>
        
        <!-- 一些文档结构检查 -->
        <xsl:template match="/">
            <xsl:if test="count(//w:customXml/ancestor-or-self::w:customXml[last()]) > 1">
                <xsl:message>生成的XML文档将不是格式良好的，将具有多个根元素。</xsl:message>
            </xsl:if>
            <!-- 处理文档内容 -->
            <xsl:apply-templates/>
        </xsl:template>
        
        <!-- 复制自定义XML元素 -->
        <xsl:template match="w:customXml">
            <xsl:element name="{@w:element}" namespace="{@w:uri}">
                <!-- 复制属性值 -->
                <xsl:for-each select="w:customXmlPr/w:attr">
                    <xsl:attribute name="{@w:name}" namespace="{@w:uri}">
                        <xsl:value-of select="@w:val"/>
                    </xsl:attribute>
                </xsl:for-each>
                <!-- 处理内容 -->
                <xsl:apply-templates/>
            </xsl:element>
        </xsl:template>
        
        <!-- 仅复制自定义XML内的文本 -->
        <xsl:template match="text()[ancestor::w:customXml[not(.//w:customXml)]]"
            priority="10">
            <xsl:value-of select="."/>
        </xsl:template>
        
        <!-- 警告混合内容 -->
        <xsl:template match="text()[ancestor::w:customXml]" priority="5">
            <xsl:choose>
                <xsl:when test="$ignoreMixedContent">
                    <xsl:message>从输出中剥离“<xsl:value-of select="."/>”。</xsl:message>
                    <xsl:message>此文本是混合内容的一部分，会导致非有效的结果。</xsl:message>
                </xsl:when>
                <xsl:otherwise>
                    <xsl:value-of select="."/>
                </xsl:otherwise>
            </xsl:choose>
        </xsl:template>
        
        <!-- 警告未标记的文本 -->
        <xsl:template match="text()">
            <xsl:message>从输出中剥离“<xsl:value-of select="."/>”。</xsl:message>
            <xsl:message>此文本未被根元素包围，会导致非格式良好的结果。</xsl:message>
        </xsl:template>
        
        <!-- 不要获取已删除的内容 -->
        <xsl:template match="w:del|w:moveFrom"/>
    </xsl:stylesheet>
    ```
    
    一旦提取了此自定义标记，生成的XML文档可以与WordprocessingML文档分开进行验证。
    
    例如，第530页上的示例的自定义XML，一旦提取，将是：
    
    ```xml
    <invoice xmlns="http://www.example.com/2006/invoice">
    <customerName>Tristan Davis</customerName>
    </invoice>
    ```
    
    应用程序可以使用任何所需的方法找到适当的模式（schema）进行验证。例如，使用此标准定义的信息的一种方法可能是：
    
    - 在文档设置部分定位schema元素([§23.2.1])，其uri属性与从自定义XML标记中提取的XML文档的根元素的命名空间匹配
    - 如果该元素还指定了schemaLocation属性，则使用生成的路径来定位用于验证的模式。
    - 一旦定位了此模式，应根据doNotValidateAgainstSchema([§17.15.1.43])的值触发验证。

=== "英文"

    The custom XML markup capabilities described in [§17.5] allow a WordprocessingML document to contain custom XML semantics beyond those specified by ECMA-376. In order to extract those semantics from within WordprocessingML content, an application may employ any desired method.
    
    As an example, an XSL transformation which performs this task is included below, which, when applied to the Main Document part, would extract any custom XML markup.
    
    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns:w="http://purl.oclc.org/ooxml/wordprocessingml/main">
    
    <!-- This parameter should have the same value as
    ignoreMixedContent settings (see 17.15.1.54 in Part 1) -->
        <xsl:param name="ignoreMixedContent" select="false()"/>
        
        <!-- Some document structure checks -->
        <xsl:template match="/">
            <xsl:if test="count(//w:customXml/ancestor-or-
                self::w:customXml[last()]) > 1">
                <xsl:message>Produced XML document will not be WF and will have more
                    then one root element.</xsl:message>
            </xsl:if>
            <!-- Process content of document -->
            <xsl:apply-templates/>
        </xsl:template>
    
        <!-- copy over custom XML elements -->
        <xsl:template match="w:customXml">
            <xsl:element name="{@w:element}" namespace="{@w:uri}">
                <!-- copy over attribute values -->
                <xsl:for-each select="w:customXmlPr/w:attr">
                    <xsl:attribute name="{@w:name}" namespace="{@w:uri}">
                        <xsl:value-of select="@w:val"/>
                    </xsl:attribute>
                </xsl:for-each>
                <!-- process content -->
                <xsl:apply-templates/>
            </xsl:element>
        </xsl:template>
        
        <!-- copy over only text inside custom XML -->
        <xsl:template match="text()[ancestor::w:customXml[not(.//w:customXml)]]"
            priority="10">
            <xsl:value-of select="."/>
        </xsl:template>
        
        <!-- warn about mixed content -->
        <xsl:template match="text()[ancestor::w:customXml]" priority="5">
            <xsl:choose>
                <xsl:when test="$ignoreMixedContent">
                    <xsl:message>Stripping "<xsl:value-of select="."/>" from
                        output.</xsl:message>
                    <xsl:message>This text is part of mixed content and would cause
                        non-valid result.</xsl:message>
                </xsl:when>
                <xsl:otherwise>
                    <xsl:value-of select="."/>
                </xsl:otherwise>
            </xsl:choose>
        </xsl:template>
        
        <!-- warn about text which is not tagged -->
        <xsl:template match="text()">
            <xsl:message>Stripping "<xsl:value-of select="."/>" from
                output.</xsl:message>
            <xsl:message>This text is not enclosed by root element and would cause
                non-WF result.</xsl:message>
        </xsl:template>
    
        <!-- do not pick up deleted content -->
        <xsl:template match="w:del|w:moveFrom"/>
    </xsl:stylesheet>
    ```
    
    Once this custom markup is extracted, the resulting XML document can be validated separately from the WordprocessingML document.
    
    For example, the custom XML for the example on p. 530, once extracted, would be:
    
    ```xml
    <invoice xmlns="http://www.example.com/2006/invoice ">
    <customerName>Tristan Davis</customerName>
    </invoice>
    ```
    
    An application can employ any desired method to find the appropriate schema(s) for validation. As an example, one such approach using information defined by this Standard might be:
    
    - Locate the schema element ([§23.2.1]) in the Document Settings part whose uri attribute matches the namespace of the root element in the XML document extracted from custom XML markup
    - If that element also specifies a schemaLocation attribute, the resulting path is used to locate the schema used for validation.
    - Once this schema is located, validation should be triggered based on the value of doNotValidateAgainstSchema ([§17.15.1.43]).

[§17.5]: ./chapter17/05custom.md
[§17.15.1.43]: ./chapter17/15settings.md#1715143-donotvalidateagainstschema-不根据架构验证自定义-xml-标记

[§23.2.1]: ./chapter-23.md#2321-schema-custom-xml-schema-reference