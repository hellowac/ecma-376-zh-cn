
# L.4.15 Diagrams

**Diagrams**

## L.4.15.1 介绍

=== "中文"

    DrawingML 绘制文件格式分为以下主题：

    - 数据模型 - Data Model
    - 颜色 - Colors
    - 快速样式 - Quick Styles
    - 布局 - Layout

=== "英文"

    **Introduction**

    The DrawingML diagram file format is broken down into the following subjects:

    - Data Model
    - Colors
    - Quick Styles
    - Layout

## L.4.15.2 元素特性合集

=== "中文"

    模式(schema) `dml-diagram.xsd` 定义了一个复杂类型 `CT_ElemPropSet`，它是一个用于保存元素特性和定制的通用类型，并且在 `DrawingML` 的某些复杂类型中被广泛使用。这个复杂类型包含许多特性，这些特性在随后的子条款中有解释。`CT_ElemPropSet` 的定义如下：

    ```xml
    <xsd:complexType name="CT_ElemPropSet">
        <xsd:sequence>
            <xsd:element name="presLayoutVars" type="CT_LayoutVariablePropertySet" minOccurs="0"
            maxOccurs="1"/>
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
        </xsd:sequence>
        <xsd:attribute name="presAssocID" type="ST_ModelId" use="optional"/>
        <xsd:attribute name="presName" type="xsd:string" use="optional"/>
        <xsd:attribute name="presStyleLbl" type="xsd:string" use="optional"/>
        <xsd:attribute name="presStyleIdx" type="xsd:int" use="optional"/>
        <xsd:attribute name="presStyleCnt" type="xsd:int" use="optional"/>
        <xsd:attribute name="loTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="loCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="qsTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="qsCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="csTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="csCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="coherent3DOff" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="phldrT" type="xsd:string" use="optional"/>
        <xsd:attribute name="phldr" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custAng" type="xsd:int" use="optional"/>
        <xsd:attribute name="custFlipVert" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custFlipHor" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custSzX" type="xsd:int" use="optional"/>
        <xsd:attribute name="custSzY" type="xsd:int" use="optional"/>
        <xsd:attribute name="custScaleX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custScaleY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custT" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custLinFactX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactNeighborX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactNeighborY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custRadScaleRad" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custRadScaleInc" type="ST_PrSetCustVal" use="optional"/>
      </xsd:complexType>
    ```

=== "英文"

    **Element Property Set**

    The schema dml-diagram.xsd defines a complex type, CT_ElemPropSet, which is a catch-all for holding element properties and customizations, and is used throughout certain complex types in DrawingML. This complex type contains many properties, and these are explained in subsequent subclauses. The definition of CT_ElemPropSet is as follows:

    ```xml
    <xsd:complexType name="CT_ElemPropSet">
        <xsd:sequence>
            <xsd:element name="presLayoutVars" type="CT_LayoutVariablePropertySet" minOccurs="0"
            maxOccurs="1"/>
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
        </xsd:sequence>
        <xsd:attribute name="presAssocID" type="ST_ModelId" use="optional"/>
        <xsd:attribute name="presName" type="xsd:string" use="optional"/>
        <xsd:attribute name="presStyleLbl" type="xsd:string" use="optional"/>
        <xsd:attribute name="presStyleIdx" type="xsd:int" use="optional"/>
        <xsd:attribute name="presStyleCnt" type="xsd:int" use="optional"/>
        <xsd:attribute name="loTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="loCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="qsTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="qsCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="csTypeId" type="xsd:string" use="optional"/>
        <xsd:attribute name="csCatId" type="xsd:string" use="optional"/>
        <xsd:attribute name="coherent3DOff" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="phldrT" type="xsd:string" use="optional"/>
        <xsd:attribute name="phldr" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custAng" type="xsd:int" use="optional"/>
        <xsd:attribute name="custFlipVert" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custFlipHor" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custSzX" type="xsd:int" use="optional"/>
        <xsd:attribute name="custSzY" type="xsd:int" use="optional"/>
        <xsd:attribute name="custScaleX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custScaleY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custT" type="xsd:boolean" use="optional"/>
        <xsd:attribute name="custLinFactX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactNeighborX" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custLinFactNeighborY" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custRadScaleRad" type="ST_PrSetCustVal" use="optional"/>
        <xsd:attribute name="custRadScaleInc" type="ST_PrSetCustVal" use="optional"/>
      </xsd:complexType>
    ```

### L.4.15.2.1 Presentation元素特性

=== "中文"

    下面的属性经由`presentation`元素体现:

    - **presLayoutVars** – 布局(layout)变量属性设置。
    - **style** – 到到样式矩阵排列的链接.
    - **presAssocID** – 与此表示元素关联的语义元素。 该 ID 与 `presName` 一起使用来创建用于表示元素索引的唯一键。
    - **presName** – 此演示元素的布局节点名称。 该名称与 `presAssocID` 一起使用来创建用于表示元素索引的唯一键。
    - **presStyleLbl** – 该呈现元素的布局节点样式标签.
    - **presStyleIdx** – 该呈现元素的布局节点样式索引.
    - **presStyleCnt** – 该展示元素的布局节点样式计数.

=== "英文"

    **Presentation Element Properties**

    The following attributes deal with presentation elements:

    - presLayoutVars – The layout variable property set.
    - style – The link to the permutation of the style matrix.
    - presAssocID – The semantic element associated with this presentation element. This ID is used     together with the presName to create a unique key for presentation element indexing.
    - presName – The layout node name of this presentation element. This name is used together     with presAssocID to create a unique key for presentation element indexing.
    - presStyleLbl – The layout node style label of this presentation element..
    - presStyleIdx – The layout node style index of this presentation element..
    - presStyleCnt – The layout node style count of this presentation element.

### L.4.15.2.2 Document元素特性

=== "中文"

    The following attributes deal with the document element:

    - loTypeID – The ID of the current diagram type.
    - loCatId – The ID of the current diagram category.
    - qsTypeID – The ID of the current style type.
    - qaCatID – The ID of the current style category.
    - csTypeID – The ID of the current color transform.
    - csCatID – The ID of the current color transform category.
    - coherent3Doff – Enables or disables coherent 3D behavior for styles that have such behavior defined.

=== "英文"

    **Document Element Properties**

    The following attributes deal with the document element:

    - loTypeID – The ID of the current diagram type.
    - loCatId – The ID of the current diagram category.
    - qsTypeID – The ID of the current style type.
    - qaCatID – The ID of the current style category.
    - csTypeID – The ID of the current color transform.
    - csCatID – The ID of the current color transform category.
    - coherent3Doff – Enables or disables coherent 3D behavior for styles that have such behavior defined.

### L.4.15.2.3 Semantic元素特性

=== "中文"

    The following attributes relate to the semantic element properties:

    - phldrT – The text used for display in the element if the placeholder flag is set to true. If this field is not set, then the default placeholder text is used.
    - phldr – Indicates that the element is a placeholder or sample item.

=== "英文"

    **Semantic Element Properties**

    The following attributes relate to the semantic element properties:

    - phldrT – The text used for display in the element if the placeholder flag is set to true. If this field is not set, then the default placeholder text is used.
    - phldr – Indicates that the element is a placeholder or sample item.

### L.4.15.2.4 定制特性

=== "中文"

    The following are customization properties or tweaks:

    - custAng – The amount rotation is customized by, in 60,000th of a degree.
    - custFlipVert – Vertical flip.
    - custFlipHor – Horizontal flip.
    - custSzX – Fixed width override for a shape, in emus.
    - custSzY – Fixed height override for a shape, in emus.
    - custScaleX – Amount that the width is scaled by, in 1,000th of a percent.
    - custScaleY – Amount that the height is scaled by, in 1,000th of a percent.
    - custT – If text has been customized then layout no longer changes it.
    - custLinFactX – A percentage of the shape width that is used for offsetting the shape, in 1,000th of a percent.
    - custLinFactY – A percentage of the shape height that is used for offsetting the shape, in 1,000th of a percent.
    - custLinFactNeighborX – A percentage of the neighbor’s height used for offsetting the shape, in 1,000th of a percent.
    - custLinFactNeighborY – A percentage of the neighbor’s height used for offsetting the shape, in 1,000th of a percent.
    - custRadScaleRad – Defines how much the radius has been scaled by, in 1,000th of a percent.
    - custRadScaleInc – Defines how much the include angle has been scaled by, in 1,000th of a percent.

=== "英文"

    **Customization Properties**

    The following are customization properties or tweaks:

    - custAng – The amount rotation is customized by, in 60,000th of a degree.
    - custFlipVert – Vertical flip.
    - custFlipHor – Horizontal flip.
    - custSzX – Fixed width override for a shape, in emus.
    - custSzY – Fixed height override for a shape, in emus.
    - custScaleX – Amount that the width is scaled by, in 1,000th of a percent.
    - custScaleY – Amount that the height is scaled by, in 1,000th of a percent.
    - custT – If text has been customized then layout no longer changes it.
    - custLinFactX – A percentage of the shape width that is used for offsetting the shape, in 1,000th of a percent.
    - custLinFactY – A percentage of the shape height that is used for offsetting the shape, in 1,000th of a percent.
    - custLinFactNeighborX – A percentage of the neighbor’s height used for offsetting the shape, in 1,000th of a percent.
    - custLinFactNeighborY – A percentage of the neighbor’s height used for offsetting the shape, in 1,000th of a percent.
    - custRadScaleRad – Defines how much the radius has been scaled by, in 1,000th of a percent.
    - custRadScaleInc – Defines how much the include angle has been scaled by, in 1,000th of a percent.

## L.4.15.3 数据模型

=== "中文"

    模式(schema) dml-diagram.xsd 定义图表中的数据模型。 数据模型的目的是双重的。 数据模型的第一个用途是保存图表中包含的信息。 例如，在下面的图 1 中，数据模型的目的是保存图表的信息“一”、“二”和“三”。

    <figure markdown>
      ![Image title](./imgs/diagram-1.png)
      <figcaption>Figure 11: Example diagram with data.</figcaption>
    </figure>

    数据模型的第二个用途是定义图的初始状态。 此初始状态由可被视为占位符数据的内容组成，应用程序使用该数据在输入任何数据之前最初显示图表。 图 2 显示了包含三个空节点的初始状态下的图表的示例。 在此示例中，占位符数据由三个节点和两个连接组成，对此进行了简短的解释。

    <figure markdown>
      ![Image title](./imgs/diagram-2.png)
      <figcaption>Figure 12: An empty diagram in its initial state.</figcaption>
    </figure>

=== "英文"

    **Data Model**

    The schema dml-diagram.xsd defines the data model in a diagram. The purpose of the data model is twofold. The first use of the data model is to hold the information contained in a diagram. For example, in figure 1 below, the purpose of the data model would be to hold the information, “one”, “two” and “three” for the diagram.

    <figure markdown>
      ![Image title](./imgs/diagram-1.png)
      <figcaption>Figure 11: Example diagram with data.</figcaption>
    </figure>

    The second use of the data model is to define an initial state of the diagram. This initial state consists of what can be thought of as placeholder data, which an application uses to display a diagram initially before any data has been entered. Figure 2 shows an example of what a diagram might look like in an initial state containing three empty nodes. In this example, the placeholder data consists of three nodes and two connections, which is explained shortly. 

    <figure markdown>
      ![Image title](./imgs/diagram-2.png)
      <figcaption>Figure 12: An empty diagram in its initial state.</figcaption>
    </figure>

### L.4.15.3.1 Structural Elements

**Structural Elements**

#### L.4.15.3.1.1 Type of Structural Element

=== "中文"

    There is a single simple type, ST_PtType, used to define the contents of this element; this is defined later. Structural elements hold the data associated with a diagram and are defined in relation to oneanother through relationship types. Seven different elements are available to the user:
    
    - doc – A document element. The document element is the root element within a diagram and can be thought of as the canvas which the diagram is drawn on.
    - node – A model element. This is the basic type of an element and can be used to hold text for example.
    - asst – This is used in hierarchy diagrams and represents an assistant element.
    - pres – A presentation element. This element defines the visual aspects associated with a node, or rather the presentation aspects of an element.
    - parTrans – A parent transition element. This element holds the data for a parent-child relationship between two elements of type node.
    - sibTrans – A sibling transition element. This element holds the data for the relationship defined between two elements of type node whom are peers of one another.
    - unknown – A type of element used to maintain backward compatibility.

=== "英文"

    **Type of Structural Element**

    There is a single simple type, ST_PtType, used to define the contents of this element; this is defined later. Structural elements hold the data associated with a diagram and are defined in relation to oneanother through relationship types. Seven different elements are available to the user:
    
    - doc – A document element. The document element is the root element within a diagram and can be thought of as the canvas which the diagram is drawn on.
    - node – A model element. This is the basic type of an element and can be used to hold text for example.
    - asst – This is used in hierarchy diagrams and represents an assistant element.
    - pres – A presentation element. This element defines the visual aspects associated with a node, or rather the presentation aspects of an element.
    - parTrans – A parent transition element. This element holds the data for a parent-child relationship between two elements of type node.
    - sibTrans – A sibling transition element. This element holds the data for the relationship defined between two elements of type node whom are peers of one another.
    - unknown – A type of element used to maintain backward compatibility.

#### L.4.15.3.1.2 Relationship Type

=== "中文"

    There are defined relationships or connections between two model elements. Four types of relationships are defined in the simple type ST_CxnType:

    - parOf – Parent-child relationship.
    - presOf – Presentation relationship.
    - presParOf – Presentation parent of relationship.
    - unknownRelationship – An unknown relationship type.

=== "英文"

    **Relationship Type**

    There are defined relationships or connections between two model elements. Four types of relationships are defined in the simple type ST_CxnType:

    - parOf – Parent-child relationship.
    - presOf – Presentation relationship.
    - presParOf – Presentation parent of relationship.
    - unknownRelationship – An unknown relationship type.

#### L.4.15.3.1.3 Element

=== "中文"

    An element is a single item, such as a node or transition in the data model. Within the realm of DrawingML, the complex type CT_Pt holds information describing an element within a diagram. Within this description lies both the data held within the element, and any formatting on that element. A CT_Pt is defined as follows:

    ```xml
    <xsd:complexType name="CT_Pt">
        <xsd:sequence>
            <xsd:element name="prSet" type="CT_ElemPropSet" minOccurs="0" maxOccurs="1" />
            <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="t" type="a:CT_TextBody" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="modelId" type="ST_ModelId" use="required" />
        <xsd:attribute name="type" type="ST_PtType" use="optional" default="node" />
        <xsd:attribute name="cxnId" type="ST_ModelId" use="optional" default="0" />
    </xsd:complexType>
    ```
    
    The attribute modelId holds a unique id for a particular element. This unique id can be referenced elsewhere, for example, from within a connection list. This attribute is required for every point defined in the data model.

    The last two attributes of the CT_Pt are optional. The first defines the type of point with the default being a node. The second defines a connection id. This connection id is only used if the point type is parTrans, or sibTrans. The connection id refers to a relationship that is defined elsewhere in the data model.

=== "英文"

    **Element**

    An element is a single item, such as a node or transition in the data model. Within the realm of DrawingML, the complex type CT_Pt holds information describing an element within a diagram. Within this description lies both the data held within the element, and any formatting on that element. A CT_Pt is defined as follows:

    ```xml
    <xsd:complexType name="CT_Pt">
        <xsd:sequence>
            <xsd:element name="prSet" type="CT_ElemPropSet" minOccurs="0" maxOccurs="1" />
            <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="t" type="a:CT_TextBody" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="modelId" type="ST_ModelId" use="required" />
        <xsd:attribute name="type" type="ST_PtType" use="optional" default="node" />
        <xsd:attribute name="cxnId" type="ST_ModelId" use="optional" default="0" />
    </xsd:complexType>
    ```
    
    The attribute modelId holds a unique id for a particular element. This unique id can be referenced elsewhere, for example, from within a connection list. This attribute is required for every point defined in the data model.

    The last two attributes of the CT_Pt are optional. The first defines the type of point with the default being a node. The second defines a connection id. This connection id is only used if the point type is parTrans, or sibTrans. The connection id refers to a relationship that is defined elsewhere in the data model.

#### L.4.15.3.1.4 Relationship

=== "中文"

    A relationship is a connection between any two model elements. An example of where a relationship would be used can be seen in figures 1 and 2. In each of those examples, the arrows between the nodes have relationships defined. A relationship is defined as follows:

    ```xml
    <xsd:complexType name="CT_Cxn">
        <xsd:attribute name="modelId" type="ST_ModelId" use="required" />
        <xsd:attribute name="type" type="ST_CxnType" use="optional" default="parOf" />
        <xsd:attribute name="srcId" type="ST_ModelId" use="required" />
        <xsd:attribute name="destId" type="ST_ModelId" use="required" />
        <xsd:attribute name="srcOrd" type="xsd:unsignedInt" use="required" />
        <xsd:attribute name="destOrd" type="xsd:unsignedInt" use="required" />
        <xsd:attribute name="parTransId" type="ST_ModelId" use="optional" default="0" />
        <xsd:attribute name="sibTransId" type="ST_ModelId" use="optional" default="0" />
        <xsd:attribute name="presId" type="xsd:string" use="optional" default="" />
    </xsd:complexType>
    ```

    The relationship, as with the element, has a unique id associated with it referred to as the modelID. The srcId and destId attributes refer to ids of the source element and destination element, respectively, that this relationship is defined between.

    The srcOrd and destOrd refer to the ordinality of siblings for a given connection. For example, if a node had three siblings, A, B, and C, then the srcOrd would define if they were to show up as A, B, C, or perhaps B, C, and then A.

    The presId attribute contains the presentation that is associated with this particular relationship.

=== "英文"

    **Relationship**

    A relationship is a connection between any two model elements. An example of where a relationship would be used can be seen in figures 1 and 2. In each of those examples, the arrows between the nodes have relationships defined. A relationship is defined as follows:

    ```xml
    <xsd:complexType name="CT_Cxn">
        <xsd:attribute name="modelId" type="ST_ModelId" use="required" />
        <xsd:attribute name="type" type="ST_CxnType" use="optional" default="parOf" />
        <xsd:attribute name="srcId" type="ST_ModelId" use="required" />
        <xsd:attribute name="destId" type="ST_ModelId" use="required" />
        <xsd:attribute name="srcOrd" type="xsd:unsignedInt" use="required" />
        <xsd:attribute name="destOrd" type="xsd:unsignedInt" use="required" />
        <xsd:attribute name="parTransId" type="ST_ModelId" use="optional" default="0" />
        <xsd:attribute name="sibTransId" type="ST_ModelId" use="optional" default="0" />
        <xsd:attribute name="presId" type="xsd:string" use="optional" default="" />
    </xsd:complexType>
    ```

    The relationship, as with the element, has a unique id associated with it referred to as the modelID. The srcId and destId attributes refer to ids of the source element and destination element, respectively, that this relationship is defined between.

    The srcOrd and destOrd refer to the ordinality of siblings for a given connection. For example, if a node had three siblings, A, B, and C, then the srcOrd would define if they were to show up as A, B, C, or perhaps B, C, and then A.

    The presId attribute contains the presentation that is associated with this particular relationship.

#### L.4.15.3.1.5 Element List

=== "中文"

    The complex type CT_PtList is simply a sequence of elements. Its definition is as follows:

    ```xml
    <xsd:complexType name="CT_PtList">
        <xsd:sequence>
            <xsd:element name="pt" type="CT_Pt" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Element List**

    The complex type CT_PtList is simply a sequence of elements. Its definition is as follows:

    ```xml
    <xsd:complexType name="CT_PtList">
        <xsd:sequence>
            <xsd:element name="pt" type="CT_Pt" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.3.1.6 Relationship List

=== "中文"

    This complex type, CT_CxnList, is simply a sequence of connections. Its definition is as follows:

    ```xml
    <xsd:complexType name="CT_CxnList" oxsd:cname="Relationships">
        <xsd:sequence>
            <xsd:element name="cxn" type="CT_Cxn" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Relationship List**

    This complex type, CT_CxnList, is simply a sequence of connections. Its definition is as follows:

    ```xml
    <xsd:complexType name="CT_CxnList" oxsd:cname="Relationships">
        <xsd:sequence>
            <xsd:element name="cxn" type="CT_Cxn" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.3.1.7 Data Model

=== "中文"

    The complex type CT_DataModel defines the data model and contains a sequence of elements. It is defined as follows:

    ```xml
    <xsd:complexType name="CT_DataModel">
        <xsd:sequence oxsd:emitArgs="flattenSequence">
            <xsd:element name="ptLst" type="CT_PtList" />
            <xsd:element name="cxnLst" type="CT_CxnList" minOccurs="0" maxOccurs="1" />
            <xsd:element name="bg" type="a:CT_BackgroundFormatting" minOccurs="0" />
            <xsd:element name="whole" type="a:CT_WholeE2oFormatting" minOccurs="0" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    The data model contains a list of elements, a list of connections, and formatting properties for the background object and the diagram container. This complex type is responsible for holding all databound information of the diagram being created.

=== "英文"

    **Data Model**

    The complex type CT_DataModel defines the data model and contains a sequence of elements. It is defined as follows:

    ```xml
    <xsd:complexType name="CT_DataModel">
        <xsd:sequence oxsd:emitArgs="flattenSequence">
            <xsd:element name="ptLst" type="CT_PtList" />
            <xsd:element name="cxnLst" type="CT_CxnList" minOccurs="0" maxOccurs="1" />
            <xsd:element name="bg" type="a:CT_BackgroundFormatting" minOccurs="0" />
            <xsd:element name="whole" type="a:CT_WholeE2oFormatting" minOccurs="0" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    The data model contains a list of elements, a list of connections, and formatting properties for the background object and the diagram container. This complex type is responsible for holding all databound information of the diagram being created.

## L.4.15.4 颜色变换

=== "中文"

    颜色变换定义颜色如何应用于图表。 颜色变换定义了整个图表中颜色的使用方式，并且它们规定了诸如使用哪种主题颜色或颜色、是否对图表的某种颜色或部分应用了色调或阴影，或者如果颜色是 甚至根本没有使用过。 图 3 展示了颜色变换对简单图表的作用的一些示例。
    
    <figure markdown>
      ![Image title](./imgs/diagram-3.png)
      <figcaption>Figure 13: Different examples of a color transform applied to a diagram</figcaption>
    </figure>

=== "英文"

    **Color Transforms**

    Color transforms define how colors are applied to diagrams. Color transforms define how color is used in the diagram as a whole, and they mandate things such as which theme color or colors are used, if there is a tint or shade applied to a certain color or part of the diagram, or if color is even used at all. Some examples of what color transforms can do to a simple diagram can be seen in figure 3.
    

    <figure markdown>
      ![Image title](./imgs/diagram-3.png)
      <figcaption>Figure 13: Different examples of a color transform applied to a diagram</figcaption>
    </figure>

### L.4.15.4.1 Structural Elements

=== "中文"

    The structural elements which come together to create a color transform, or rather, the complex type CT_ColorTransform, are as follows:

    - CT_CTName
    - CT_CTDescription
    - CT_CTCategory
    - CT_CTCategories
    - ST_ClrAppMethod
    - ST_HueDir
    - CT_Colors
    - CT_CTStyleLabel
    - CT_CTVersion
    - CT_ColorTransformHeader
    - CT_ColorTransformHeaderLst

    The complex types CT_CTName (name), CT_CTDescription (description), CT_CTCategory (category), and CT_CTCategories (list of categories) work together to name, describe and categorize the particular color transform. These complex types are mirrored elsewhere throughout DrawingML in the different subjects in order to perform the same tasks of naming, describing, and categorizing.

    The name consists simply of two strings, one of a name for the color transform, which is required, and an optional language tag. The language allows someone to specify a language for a given title. It is possible to specify multiple titles that are language dependant. The description also has the optional language attribute as in the name, along with a second required string attribute which holds the actual description. The usage of this is exactly the same as within CT_CTName. CT_CTName and CT_CTDescription are defined in the following way:

    ```xml
    <xsd:complexType name="CT_CTName">
        <xsd:attribute name="lang" type="xsd:string" use="optional" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    <xsd:complexType name="CT_CTDescription">
        <xsd:attribute name="lang" type="xsd:string" use="optional" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

    The category and categories complex types , CT_CTCategory and CT_CTCategories, respectively, define how the color transform is categorized within the user interface of the application. The category contains a name, or type, along with a priority that defines the ordering of the color transform. The lower the priority, the earlier in the category it displays. If there is a tie, the unique id associated with the color transform decides the order alphabetically. CT_CTCategories is simply a list of CT_CTCategory. The two complex types are defined as follows:

    ```xml
    <xsd:complexType name="CT_CTCategory">
        <xsd:attribute name="type" type="xsd:anyURI" use="required" />
        <xsd:attribute name="pri" type="xsd:unsignedInt" use="required" />
    </xsd:complexType>
    <xsd:complexType name="T_CTCategories">
        <xsd:sequence minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="cat" type="CT_CTCategory" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Structural Elements**

    The structural elements which come together to create a color transform, or rather, the complex type CT_ColorTransform, are as follows:

    - CT_CTName
    - CT_CTDescription
    - CT_CTCategory
    - CT_CTCategories
    - ST_ClrAppMethod
    - ST_HueDir
    - CT_Colors
    - CT_CTStyleLabel
    - CT_CTVersion
    - CT_ColorTransformHeader
    - CT_ColorTransformHeaderLst

    The complex types CT_CTName (name), CT_CTDescription (description), CT_CTCategory (category), and CT_CTCategories (list of categories) work together to name, describe and categorize the particular color transform. These complex types are mirrored elsewhere throughout DrawingML in the different subjects in order to perform the same tasks of naming, describing, and categorizing.

    The name consists simply of two strings, one of a name for the color transform, which is required, and an optional language tag. The language allows someone to specify a language for a given title. It is possible to specify multiple titles that are language dependant. The description also has the optional language attribute as in the name, along with a second required string attribute which holds the actual description. The usage of this is exactly the same as within CT_CTName. CT_CTName and CT_CTDescription are defined in the following way:

    ```xml
    <xsd:complexType name="CT_CTName">
        <xsd:attribute name="lang" type="xsd:string" use="optional" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    <xsd:complexType name="CT_CTDescription">
        <xsd:attribute name="lang" type="xsd:string" use="optional" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

    The category and categories complex types , CT_CTCategory and CT_CTCategories, respectively, define how the color transform is categorized within the user interface of the application. The category contains a name, or type, along with a priority that defines the ordering of the color transform. The lower the priority, the earlier in the category it displays. If there is a tie, the unique id associated with the color transform decides the order alphabetically. CT_CTCategories is simply a list of CT_CTCategory. The two complex types are defined as follows:

    ```xml
    <xsd:complexType name="CT_CTCategory">
        <xsd:attribute name="type" type="xsd:anyURI" use="required" />
        <xsd:attribute name="pri" type="xsd:unsignedInt" use="required" />
    </xsd:complexType>
    <xsd:complexType name="T_CTCategories">
        <xsd:sequence minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="cat" type="CT_CTCategory" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.4.1.1 Color Application Method

=== "中文"

    The simple type ST_ClrAppMethod lists the different options for color to be applied to a diagram. There are three options available to the user: span, cycle, and repeat. Given a list of colors, which go from color A to color B, the differences in these three options can be defined. These options are shown below in Figure 4. 

    The span option, from the start of the diagram to the end of the diagram, interpolates between the colors A through B for every node along the way.
    
    The cycle option interpolates from A to B then back to A from the start of the diagram to the end of the diagram.
    
    The repeat option applies colors A through B one at a time for each point in the diagram, then repeats A through B as needed.
    

    <figure markdown>
      ![Image title](./imgs/diagram-4.png)
      <figcaption>Figure 14: Examples of the three different ways a color transform is applied to a diagram.</figcaption>
    </figure>

=== "英文"

    **Color Application Method**

    The simple type ST_ClrAppMethod lists the different options for color to be applied to a diagram. There are three options available to the user: span, cycle, and repeat. Given a list of colors, which go from color A to color B, the differences in these three options can be defined. These options are shown below in Figure 4. 

    The span option, from the start of the diagram to the end of the diagram, interpolates between the colors A through B for every node along the way.
    
    The cycle option interpolates from A to B then back to A from the start of the diagram to the end of the diagram.
    
    The repeat option applies colors A through B one at a time for each point in the diagram, then repeats A through B as needed.

    <figure markdown>
      ![Image title](./imgs/diagram-4.png)
      <figcaption>Figure 14: Examples of the three different ways a color transform is applied to a diagram.</figcaption>
    </figure>

#### L.4.15.4.1.2 Hue Direction

=== "中文"

    The simple type ST_HueDir defines the direction of a hue color shift around a color wheel. A user can either define the shift to occur in the clockwise (cw) direction, or in the counterclockwise (ccw) direction. For example, in Figure 4, the span colors are red and green. The behavior shown in figure 4 is a shift in the cw direction. If the hue shift had been defined in the ccw direction, the colors interpolated between colors A and B would have been in the hues purple and blue. Another example of a hue direction shift in the clockwise can be seen in Figure 5 below along with the color shift from red to yellow and then from yellow to blue along the primary colors. Counterclockwise shifts would occur in the direction of yellow to red and blue to yellow in the examples below.
    

    <figure markdown>
      ![Image title](./imgs/diagram-5.png)
      <figcaption>Figure 15: Example hue shifts in the clockwise direction around a color wheel applied to two diagrams. The three primary colors, red, yellow, and blue are used to represent the three major sections of a color wheel which ranges between red to yellow to blue to red.</figcaption>
    </figure>

=== "英文"

    **Hue Direction**

    The simple type ST_HueDir defines the direction of a hue color shift around a color wheel. A user can either define the shift to occur in the clockwise (cw) direction, or in the counterclockwise (ccw) direction. For example, in Figure 4, the span colors are red and green. The behavior shown in figure 4 is a shift in the cw direction. If the hue shift had been defined in the ccw direction, the colors interpolated between colors A and B would have been in the hues purple and blue. Another example of a hue direction shift in the clockwise can be seen in Figure 5 below along with the color shift from red to yellow and then from yellow to blue along the primary colors. Counterclockwise shifts would occur in the direction of yellow to red and blue to yellow in the examples below.
    

    <figure markdown>
      ![Image title](./imgs/diagram-5.png)
      <figcaption>Figure 15: Example hue shifts in the clockwise direction around a color wheel applied to two diagrams. The three primary colors, red, yellow, and blue are used to represent the three major sections of a color wheel which ranges between red to yellow to blue to red.</figcaption>
    </figure>

#### L.4.15.4.1.3 Colors

=== "中文"

    The complex type CT_Colors holds the actual color values that are to be applied to a given diagram and how those colors are to be applied. It contains the color application method and hue shift direction, and is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_Colors">
        <xsd:sequence>
            <xsd:group ref="a:EG_ColorChoice" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="meth" type="ST_ClrAppMethod" use="optional" default="span" />
        <xsd:attribute name="hueDir" type="ST_HueDir" use="optional" default="cw" />
    </xsd:complexType>
    ```

    The sequence of colors is defined via the sequence of EG_ColorChoices.

=== "英文"

    **Colors**

    The complex type CT_Colors holds the actual color values that are to be applied to a given diagram and how those colors are to be applied. It contains the color application method and hue shift direction, and is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_Colors">
        <xsd:sequence>
            <xsd:group ref="a:EG_ColorChoice" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="meth" type="ST_ClrAppMethod" use="optional" default="span" />
        <xsd:attribute name="hueDir" type="ST_HueDir" use="optional" default="cw" />
    </xsd:complexType>
    ```

    The sequence of colors is defined via the sequence of EG_ColorChoices.

#### L.4.15.4.1.4 Style Label

=== "中文"

    The complex type CT_CTStyleLabel packages together colors for the different pieces of a diagram. There are six different aspects to a diagram that can be colored independently of one another. Each of the six parts is of complex type CT_Colors. They are:

    - Fill Colors – The colors that actually fill the shapes in the diagram
    - Line Colors – The colors of the lines on the shapes in the diagram.
    - Effect Colors – The colors of the effects applied to the shapes within the diagram (eg. Glow).
    - Text Line Colors – The colors of the lines on the text within the diagram.
    - Text Fill Colors – The color of the text within the diagram.
    - Text Effect Colors – The colors of the effects applied to the text within the diagram.
    
    The final piece of a style label is simply its name, which is a string. CT_CTStyleLabel is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_CTStyleLabel">
        <xsd:sequence>
            <xsd:element name="fillClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="linClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="effectClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txLinClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txFillClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txEffectClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

=== "英文"

    **Style Label**

    The complex type CT_CTStyleLabel packages together colors for the different pieces of a diagram. There are six different aspects to a diagram that can be colored independently of one another. Each of the six parts is of complex type CT_Colors. They are:

    - Fill Colors – The colors that actually fill the shapes in the diagram
    - Line Colors – The colors of the lines on the shapes in the diagram.
    - Effect Colors – The colors of the effects applied to the shapes within the diagram (eg. Glow).
    - Text Line Colors – The colors of the lines on the text within the diagram.
    - Text Fill Colors – The color of the text within the diagram.
    - Text Effect Colors – The colors of the effects applied to the text within the diagram.
    
    The final piece of a style label is simply its name, which is a string. CT_CTStyleLabel is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_CTStyleLabel">
        <xsd:sequence>
            <xsd:element name="fillClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="linClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="effectClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txLinClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txFillClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txEffectClrLst" type="CT_Colors" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

#### L.4.15.4.1.5 Version

=== "中文"

    The simple type ST_CTVersion defines the minimum version of an application that the color transform works with. The version corresponds to build numbers in the major.minor.build.revision format and is defined as follows:

    `([0-9]?[0-9])?(\.[0-9]?[0-9])?(\.[0-9]{4})?(\.[0-9]{4})`

=== "英文"

    **Version**

    The simple type ST_CTVersion defines the minimum version of an application that the color transform works with. The version corresponds to build numbers in the major.minor.build.revision format and is defined as follows:

    `([0-9]?[0-9])?(\.[0-9]?[0-9])?(\.[0-9]{4})?(\.[0-9]{4})`

#### L.4.15.4.1.6 Color Transform

=== "中文"

    The complex type CT_ColorTransform brings together all of the pieces into one cohesive structure. This is the actual definition of a color transform, which can be applied to any diagram; it is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_ColorTransform">
        <xsd:sequence>
            <xsd:element name="title" type="CT_CTName" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_CTDescription" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_CTCategories" minOccurs="0" />
            <xsd:element name="styleLbl" type="CT_CTStyleLabel" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_CTVersion" use="optional" default="12.0" />
    </xsd:complexType>
    ```
    
    A color transform contains a title, description, category list, and style label in a sequence along with a unique id and a minimum version.

=== "英文"

    **Color Transform**

    The complex type CT_ColorTransform brings together all of the pieces into one cohesive structure. This is the actual definition of a color transform, which can be applied to any diagram; it is defined as follows:
    
    ```xml
    <xsd:complexType name="CT_ColorTransform">
        <xsd:sequence>
            <xsd:element name="title" type="CT_CTName" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_CTDescription" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_CTCategories" minOccurs="0" />
            <xsd:element name="styleLbl" type="CT_CTStyleLabel" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_CTVersion" use="optional" default="12.0" />
    </xsd:complexType>
    ```
    
    A color transform contains a title, description, category list, and style label in a sequence along with a unique id and a minimum version.

### L.4.15.4.2 Color Transform Header

=== "中文"

    Two complex types, CT_ColorTransformHeader and CT_ColortransformHeaderLst, help alleviate potential performance concerns with initially loading in a large number of color transforms. The header information contains the minimum information required to load a color transform into the application. Because of this, color transforms themselves can be loaded only when needed, and other initialization work can progress quickly without loading unneeded information.
    
    CT_ColorTransformHeader contains information about the title of the color transform, the description, how it is categorized, the unique id, minimum version, and resId. It is defined in the following way:

    ```xml
    <xsd:complexType name="CT_ColorTransformHeader">
        <xsd:sequence>
            <xsd:element name="title" type="CT_CTName" minOccurs="1" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_CTDescription" minOccurs="1" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="T_CTCategories" minOccurs="0" o:cname="categories" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="required" />
        <xsd:attribute name="minVer" type="ST_CTVersion" use="optional" default="12.0" />
        <xsd:attribute name="resId" type="xsd:int" use="optional" default="0" />
    </xsd:complexType>
    ```

    The complex type CT_ColorTransformHeaderLst simply contains a list of color transform headers. It is defined as follows:

    ```xml
    <xsd:complexType name="CT_ColorTransformHeaderLst">
        <xsd:sequence>
            <xsd:element name="colorsDefHdr" type="CT_ColorTransformHeader" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Color Transform Header**

    Two complex types, CT_ColorTransformHeader and CT_ColortransformHeaderLst, help alleviate potential performance concerns with initially loading in a large number of color transforms. The header information contains the minimum information required to load a color transform into the application. Because of this, color transforms themselves can be loaded only when needed, and other initialization work can progress quickly without loading unneeded information.
    
    CT_ColorTransformHeader contains information about the title of the color transform, the description, how it is categorized, the unique id, minimum version, and resId. It is defined in the following way:

    ```xml
    <xsd:complexType name="CT_ColorTransformHeader">
        <xsd:sequence>
            <xsd:element name="title" type="CT_CTName" minOccurs="1" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_CTDescription" minOccurs="1" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="T_CTCategories" minOccurs="0" o:cname="categories" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="required" />
        <xsd:attribute name="minVer" type="ST_CTVersion" use="optional" default="12.0" />
        <xsd:attribute name="resId" type="xsd:int" use="optional" default="0" />
    </xsd:complexType>
    ```

    The complex type CT_ColorTransformHeaderLst simply contains a list of color transform headers. It is defined as follows:

    ```xml
    <xsd:complexType name="CT_ColorTransformHeaderLst">
        <xsd:sequence>
            <xsd:element name="colorsDefHdr" type="CT_ColorTransformHeader" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

## L.4.15.5 样式定义

=== "中文"

    样式定义类似于颜色变换。 样式定义定义了诸如所使用的字体、轮廓线的粗细、图表上的 3-D 属性等项目。 样式定义与颜色变换结合使用，为图表提供整体外观和感觉。 图 5 中显示了一些正在使用的样式定义示例。

    <figure markdown>
      ![Image title](./imgs/diagram-6.png)
      <figcaption>Figure 16: 在图表上使用三种不同样式定义的示例.</figcaption>
    </figure>

=== "英文"

    **Style Definition**

    A style definition is similar to a color transform. A style definition defines items such as the font used, the thickness of a contour line, 3-D properties on the diagram, among other things. Style definitions work in combination with color transforms to give an overall look and feel for the diagram. Some examples of style definitions in use are in figure 5.

    <figure markdown>
      ![Image title](./imgs/diagram-6.png)
      <figcaption>Figure 16: Examples of using three different style definitions on a diagram.</figcaption>
    </figure>

### L.4.15.5.1 Structural Elements

=== "中文"

    The structural elements which come together to create a style definition are as follows:

    - CT_SDName
    - CT_SDDescription
    - CT_SDCategory
    - CT_SDCategories
    - CT_TextProps
    - CT_StyleLabel
    - ST_SDVersion
    - CT_StyleDefinition
    - CT_StyleDefinitionHeader
    - CT_StyleDefinitionHeaderLst

    CT_SDName, CT_SDDescription, CT_SDCategory, CT_SDCategories, and ST_SDVersion are all defined exactly as they are within color transforms. These complex types were recreated within the style definition area to allow slight differentiations to be made, although, at this time they are defined exactly the same.

    The text properties, style label, and then the style definition combine together to create a style definition, which is applied to a diagram.

=== "英文"

    **Structural Elements**

    The structural elements which come together to create a style definition are as follows:

    - CT_SDName
    - CT_SDDescription
    - CT_SDCategory
    - CT_SDCategories
    - CT_TextProps
    - CT_StyleLabel
    - ST_SDVersion
    - CT_StyleDefinition
    - CT_StyleDefinitionHeader
    - CT_StyleDefinitionHeaderLst

    CT_SDName, CT_SDDescription, CT_SDCategory, CT_SDCategories, and ST_SDVersion are all defined exactly as they are within color transforms. These complex types were recreated within the style definition area to allow slight differentiations to be made, although, at this time they are defined exactly the same.

    The text properties, style label, and then the style definition combine together to create a style definition, which is applied to a diagram.

#### L.4.15.5.1.1 Text Properties

=== "中文"

    The complex type CT_TextProps holds any 3-D associated properties of the text that is to be held in the diagram. A CT_TextProps is defined as follows:

    ```xml
    <xsd:complexType name="CT_TextProps">
        <xsd:sequence>
            <xsd:group ref="a:EG_Text3D" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    All that is contained within the text properties is an EG_Text3D complex type. The usage of the text properties complex type allows 3-D text properties to be defined for a diagram style.

=== "英文"

    **Text Properties**

    The complex type CT_TextProps holds any 3-D associated properties of the text that is to be held in the diagram. A CT_TextProps is defined as follows:

    ```xml
    <xsd:complexType name="CT_TextProps">
        <xsd:sequence>
            <xsd:group ref="a:EG_Text3D" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    All that is contained within the text properties is an EG_Text3D complex type. The usage of the text properties complex type allows 3-D text properties to be defined for a diagram style.

#### L.4.15.5.1.2 Style Label

=== "中文"

    The style label contains information pertaining to the styleable elements within a diagram. These elements include the shape properties and text properties along with any references to the style matrix or document theme. The shape properties are defined in two different ways: the scene3d element that pertains to the scene on a whole (and includes lighting effects, rotations, and the like), and any 3-D and material settings are held in the sp3d element. CT_StyleLabel is defined as follows:

    ```xml
    <xsd:complexType name="CT_StyleLabel">
        <xsd:sequence>
            <xsd:element name="scene3d" type="a:CT_Scene3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="sp3d" type="a:CT_Shape3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txPr" type="CT_TextProps" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

    As with many other complex types, the style label has an attribute reserved for a name. This is simply a string that names the particular style label. This style label can then be referenced from within a diagram definition, as we can see below.

    Note that the scene3d element contained within a style label acts on the level of an individual shape, rather than the diagram as a whole. A second scene3d element is defined within the style definition; that acts on the diagram level and allows for scene coherent 3-D to be applied to the diagram. A style definition contains a style label.

=== "英文"

    **Style Label**

    The style label contains information pertaining to the styleable elements within a diagram. These elements include the shape properties and text properties along with any references to the style matrix or document theme. The shape properties are defined in two different ways: the scene3d element that pertains to the scene on a whole (and includes lighting effects, rotations, and the like), and any 3-D and material settings are held in the sp3d element. CT_StyleLabel is defined as follows:

    ```xml
    <xsd:complexType name="CT_StyleLabel">
        <xsd:sequence>
            <xsd:element name="scene3d" type="a:CT_Scene3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="sp3d" type="a:CT_Shape3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="txPr" type="CT_TextProps" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

    As with many other complex types, the style label has an attribute reserved for a name. This is simply a string that names the particular style label. This style label can then be referenced from within a diagram definition, as we can see below.

    Note that the scene3d element contained within a style label acts on the level of an individual shape, rather than the diagram as a whole. A second scene3d element is defined within the style definition; that acts on the diagram level and allows for scene coherent 3-D to be applied to the diagram. A style definition contains a style label.

#### L.4.15.5.1.3 Style Definition

=== "中文"

    The style definition complex type, CT_StyleDefinition, is the root element used to define a style definition. As with the root element of a color transform, within the style definition there exists a tite, description, category, unique id, and minimum version number. These elements serve the same purpose as they do within the color transform.
    
    The interesting aspects of a style definition complex type are that it holds a style label, another style index (which is contained within the style label as well), and another scene3d (which is also contained within the style label as has been previously mentioned). The scene3d element applies to the diagram on a whole and allows for scene coherent 3-D to be applied to the diagram. The duplication of the style index is two-fold. If a style index is not defined within the style label, then the default style index, or rather, the index defined in this complex type is used. Since a diagram definition can reference a style label, and not a style definition, the style index is also required within the style label. A CT_StyleDefinition is defined as follows:

    ```xml
    <xsd:complexType name="CT_StyleDefinition">
        <xsd:sequence>
            <xsd:element name="title" type="CT_SDName" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_SDDescription" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_SDCategories" minOccurs="0" />
            <xsd:element name="scene3d" type="a:CT_Scene3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="styleLbl" type="CT_StyleLabel" minOccurs="1" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_SDVersion" use="optional" default="12.0" />
    </xsd:complexType>
    ```

=== "英文"

    **Style Definition**

    The style definition complex type, CT_StyleDefinition, is the root element used to define a style definition. As with the root element of a color transform, within the style definition there exists a tite, description, category, unique id, and minimum version number. These elements serve the same purpose as they do within the color transform.
    
    The interesting aspects of a style definition complex type are that it holds a style label, another style index (which is contained within the style label as well), and another scene3d (which is also contained within the style label as has been previously mentioned). The scene3d element applies to the diagram on a whole and allows for scene coherent 3-D to be applied to the diagram. The duplication of the style index is two-fold. If a style index is not defined within the style label, then the default style index, or rather, the index defined in this complex type is used. Since a diagram definition can reference a style label, and not a style definition, the style index is also required within the style label. A CT_StyleDefinition is defined as follows:

    ```xml
    <xsd:complexType name="CT_StyleDefinition">
        <xsd:sequence>
            <xsd:element name="title" type="CT_SDName" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_SDDescription" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_SDCategories" minOccurs="0" />
            <xsd:element name="scene3d" type="a:CT_Scene3D" minOccurs="0" maxOccurs="1" />
            <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="styleLbl" type="CT_StyleLabel" minOccurs="1" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_SDVersion" use="optional" default="12.0" />
    </xsd:complexType>
    ```

#### L.4.15.5.1.4 Style Definition Header

=== "中文"

    The complex types CT_StyleDefinitionHeader and CT_StyleDefinitionHeaderLst perform the same function as the two complex header types in color transforms. They are used to pre-load required information so the actual loading of the style definition can happen only when needed.

=== "英文"

    **Style Definition Header**

    The complex types CT_StyleDefinitionHeader and CT_StyleDefinitionHeaderLst perform the same function as the two complex header types in color transforms. They are used to pre-load required information so the actual loading of the style definition can happen only when needed.

## L.4.15.6 布局

=== "中文"

    DrawingML 最大的一个方面是布局。 最终，布局负责定义图表除颜色和样式之外的所有方面。 它定义了图表的外观、行为方式以及数据的映射方式。 图 6 显示了布局如何创建包含数据“1”、“2”和“3”的图表的不同示例。

    <figure markdown>
      ![Image title](./imgs/diagram-7.png)
      <figcaption>Figure 17: 将数据 1、2 和 3 映射到四个不同图表的不同布局</figcaption>
    </figure>

    布局有两个方面：定义图表定义所使用的众多复杂类型，以及图表定义本身。 图表定义是布局的基本部分，并利用一切来定义新图表。

=== "英文"

    **Layout**

    The single largest aspect of DrawingML is Layout. Ultimately, layout is responsible for defining all aspects of the diagram outside of color and style. It defines how the diagram looks, how it behaves, and how the data is to be mapped. Figure 6 shows different examples of how layout works to create a diagram holding the data ‘1’, ‘2’, and ‘3’.

    <figure markdown>
      ![Image title](./imgs/diagram-7.png)
      <figcaption>Figure 17: Different layouts mapping the data 1, 2, and 3 to four different diagrams</figcaption>
    </figure>

    There are two aspects to layout: defining the numerous complex types utilized by diagram definitions, and the diagram definitions themselves. Diagram definitions are a fundamental part of layout, and utilize everything in order to define new diagrams.

### L.4.15.6.1 Basic Layout Types

=== "中文"

    There are a very large number of simple types defined in this subject. These simple types are all associated with properties of a diagram that can be modified to create a desired behavior. These simple types, along with an explanation of what each does, follow.

=== "英文"

    **Basic Layout Types**

    There are a very large number of simple types defined in this subject. These simple types are all associated with properties of a diagram that can be modified to create a desired behavior. These simple types, along with an explanation of what each does, follow.

#### L.4.15.6.1.1 Algorithm Type

=== "中文"

    ST_AlgorithmType is responsible for which algorithm is used to layout the diagram. The algorithm layout chosen determines if the diagram behaves as if it were a simple list, a circular cycle, or some other type of diagram. The algorithms available are:
    
    - unknown – Unknown algorithm type. This type is used for extensibility reasons. Use of this algorithm type can used by future versions/implementations which define new algorithm types other than the above mentioned algorithm types. By using this type, the current implementations know that they are not able to correctly render the diagram if they have only implemented the above mentioned algorithms for layout.
    - composite – The composite algorithm specifies the size and position for all child layout nodes. You can use it to create graphics with a predetermined layout or in combination with other algorithms to create more complex shapes.
    - conn – the connector algorithm lays out and routes connecting lines, arrows, and shapes between layout nodes
    - cycle – the cycle algorithm lays out child layout nodes around a circle or portion of a circle using equal angle spacing
    - hierChild – the hierarchy child algorithm works with the hierRoot algorithm to create hierarchical tree layouts. This algorithm aligns and positions its child layout nodes in a linear path under the hierRoot layout node.
    - hierRoot – the hierarchy root algorithm works with the hierChild algorithm to create
    hierarchical tree layouts. The hierRoot algorithm aligns and positions the hierRoot layout node in relation to the hierChild layout nodes.
    - pyra – the pyramid algorithm lays out child layout nodes along a vertical path and works with the trapezoid shape to create a pyramid
    - lin – the linear algorithm lays out child layout nodes along a linear path
    - sp – the space algorithm is used to specify a minimum space between other layout nodes or as an indication to do nothing with the layout node’s size and position
    - tx – manges layout of text within a shape
    - snake – the snake algorithm lays out child layout nodes along a linear path in two dimensions, allowing the linear flow to continue across multiple rows or columns

=== "英文"

    **Algorithm Type**

    ST_AlgorithmType is responsible for which algorithm is used to layout the diagram. The algorithm layout chosen determines if the diagram behaves as if it were a simple list, a circular cycle, or some other type of diagram. The algorithms available are:
    
    - unknown – Unknown algorithm type. This type is used for extensibility reasons. Use of this algorithm type can used by future versions/implementations which define new algorithm types other than the above mentioned algorithm types. By using this type, the current implementations know that they are not able to correctly render the diagram if they have only implemented the above mentioned algorithms for layout.
    - composite – The composite algorithm specifies the size and position for all child layout nodes. You can use it to create graphics with a predetermined layout or in combination with other algorithms to create more complex shapes.
    - conn – the connector algorithm lays out and routes connecting lines, arrows, and shapes between layout nodes
    - cycle – the cycle algorithm lays out child layout nodes around a circle or portion of a circle using equal angle spacing
    - hierChild – the hierarchy child algorithm works with the hierRoot algorithm to create hierarchical tree layouts. This algorithm aligns and positions its child layout nodes in a linear path under the hierRoot layout node.
    - hierRoot – the hierarchy root algorithm works with the hierChild algorithm to create
    hierarchical tree layouts. The hierRoot algorithm aligns and positions the hierRoot layout node in relation to the hierChild layout nodes.
    - pyra – the pyramid algorithm lays out child layout nodes along a vertical path and works with the trapezoid shape to create a pyramid
    - lin – the linear algorithm lays out child layout nodes along a linear path
    - sp – the space algorithm is used to specify a minimum space between other layout nodes or as an indication to do nothing with the layout node’s size and position
    - tx – manges layout of text within a shape
    - snake – the snake algorithm lays out child layout nodes along a linear path in two dimensions, allowing the linear flow to continue across multiple rows or columns

#### L.4.15.6.1.2 Axis Type

=== "中文"

    The simple type ST_AxisType defines how layout maps data to the diagram for a given point in the diagram. The different ways this can be mapped is as follows:

    - self – the layout maps to the current data point
    - ch – the layout node can map to the children of the current data point, but not to descendants lower in the hierarchy
    - des – the layout node can map to a descendant of the current data point
    - desOrSelf – the layout node can map the current data point, or to a descendant of the current data point
    - par – the layout node maps to the parent data point
    - ancst – the layout node can map to the ancestors of the current data point (parents, grandparents, great grandparents, etc)
    - ancstOrSelf – the layout node can map an ancestor data point or the current data point
    - followSib – the layout node can map to a following sibling peer to the current data point
    - precedSib – the layout node can map to a preceding sibling peer to the current data point.
    - root – the layout node can map to the root
    - none – the layout node doesn’t map to any data point

=== "英文"

    **Axis Type**

    The simple type ST_AxisType defines how layout maps data to the diagram for a given point in the diagram. The different ways this can be mapped is as follows:

    - self – the layout maps to the current data point
    - ch – the layout node can map to the children of the current data point, but not to descendants lower in the hierarchy
    - des – the layout node can map to a descendant of the current data point
    - desOrSelf – the layout node can map the current data point, or to a descendant of the current data point
    - par – the layout node maps to the parent data point
    - ancst – the layout node can map to the ancestors of the current data point (parents, grandparents, great grandparents, etc)
    - ancstOrSelf – the layout node can map an ancestor data point or the current data point
    - followSib – the layout node can map to a following sibling peer to the current data point
    - precedSib – the layout node can map to a preceding sibling peer to the current data point.
    - root – the layout node can map to the root
    - none – the layout node doesn’t map to any data point

#### L.4.15.6.1.3 Boolean Operators

=== "中文"

    Boolean operators, defined by ST_BoolOperator, are for layout.

    - none – no operator defined
    - equ – ‘equal to’ operator, returns true if the two compared values are equal, false otherwise
    - gte – ‘greater than or equal to’ operator
    - lte – ‘less than or equal to’ operator

=== "英文"

    **Boolean Operators**

    Boolean operators, defined by ST_BoolOperator, are for layout.

    - none – no operator defined
    - equ – ‘equal to’ operator, returns true if the two compared values are equal, false otherwise
    - gte – ‘greater than or equal to’ operator
    - lte – ‘less than or equal to’ operator

#### L.4.15.6.1.4 Child Order Type

=== "中文"

    The simple type ST_ChildOrderType specifices the child order type for a layout node. 

    - b – bottom
    - t – top

=== "英文"

    **Child Order Type**

    The simple type ST_ChildOrderType specifices the child order type for a layout node. 

    - b – bottom
    - t – top

#### L.4.15.6.1.5 Constraint Types

=== "中文"

    The simple type ST_ConstraintTypes defines the constraints that can be used as limits or modifications to the diagram or the nodes held within the diagram. These constraints manage the behavior of many properties that can be defined within the diagram. The different constraints that can be applied to a diagram are as follows:

    - unknown – An unknown constraint. This can be used by implementing applications to define a constraint type outside of the scope of what is defined by this simple type.
    - alignOff – specifies the alignment offset
    - begMarg – specifies the beginning margin
    - bendDist – specifies the distance at which a connector bends
    - begPad – specifies the distance between the edge of the transition node and the connector shape
    - b – bottom alignment
    - bMarg – the bottom margin
    - bOff – specifies the amount of offset relative to the bottom of the node
    - ctrX – specifies the center of the node in the X-direction
    - ctrXOff – specifies the amount of offset of the center of the node in the X-direction
    - ctrY – specifies the center of the node in the Y-direction
    - ctrYOff – specifies the amount of offset of the center of the node in the Y-direction
    - connDist – specifies the distance between connectors. Intended for use with boolean and reference constraints. Overrides values specified in the layout definition part
    - diam – specifies the diameter, and is used within the cycle algorithm type
    - endMarg – specifies the end margins
    - endPad – specifies the distance between the edge of the transition node and the connector shape
    - h – specifies the height
    - hArH – specifies the arrowhead height
    - hOff – specifies the height offset
    - l – specifies the left
    - lMarg – specifies the amount of left margin
    - lOff – specifies the amount of left offset
    - r – specifies right
    - rMarg – specifies the amount of right margin
    - rOff – specifies the amount of right offset
    - primFontSz – specifies the primary font size
    - pyraAcctRatio - specifies the fraction of the width of the diagram that is reserved for the flyouts at their shortest distance
    - secFontSiz – specifies the secondary font size
    - stemThick – specifies the thickness of the shaft on an arrow
    - t – specifies the top
    - tMarg – specifies the amount of top margin
    - tOff – specifies the amount of top offset
    - userA through userZ – User defined information. This set of enumerations allow a user to define specific values which can be referenced at a later time within a diagram definition. For example, if the value 5.1 was important to the layout and definition of a diagram, the user could define userA to be equal to 5.1 and then use the userA constraint within the diagram definition. This would allow a single place to update the value across the entire diagram definition.
    - w – specifies the width
    - wArH – specifies the width of an arrowhead
    - wOff – specifies the amount of width offset

=== "英文"

    **Constraint Types**

    The simple type ST_ConstraintTypes defines the constraints that can be used as limits or modifications to the diagram or the nodes held within the diagram. These constraints manage the behavior of many properties that can be defined within the diagram. The different constraints that can be applied to a diagram are as follows:

    - unknown – An unknown constraint. This can be used by implementing applications to define a constraint type outside of the scope of what is defined by this simple type.
    - alignOff – specifies the alignment offset
    - begMarg – specifies the beginning margin
    - bendDist – specifies the distance at which a connector bends
    - begPad – specifies the distance between the edge of the transition node and the connector shape
    - b – bottom alignment
    - bMarg – the bottom margin
    - bOff – specifies the amount of offset relative to the bottom of the node
    - ctrX – specifies the center of the node in the X-direction
    - ctrXOff – specifies the amount of offset of the center of the node in the X-direction
    - ctrY – specifies the center of the node in the Y-direction
    - ctrYOff – specifies the amount of offset of the center of the node in the Y-direction
    - connDist – specifies the distance between connectors. Intended for use with boolean and reference constraints. Overrides values specified in the layout definition part
    - diam – specifies the diameter, and is used within the cycle algorithm type
    - endMarg – specifies the end margins
    - endPad – specifies the distance between the edge of the transition node and the connector shape
    - h – specifies the height
    - hArH – specifies the arrowhead height
    - hOff – specifies the height offset
    - l – specifies the left
    - lMarg – specifies the amount of left margin
    - lOff – specifies the amount of left offset
    - r – specifies right
    - rMarg – specifies the amount of right margin
    - rOff – specifies the amount of right offset
    - primFontSz – specifies the primary font size
    - pyraAcctRatio - specifies the fraction of the width of the diagram that is reserved for the flyouts at their shortest distance
    - secFontSiz – specifies the secondary font size
    - stemThick – specifies the thickness of the shaft on an arrow
    - t – specifies the top
    - tMarg – specifies the amount of top margin
    - tOff – specifies the amount of top offset
    - userA through userZ – User defined information. This set of enumerations allow a user to define specific values which can be referenced at a later time within a diagram definition. For example, if the value 5.1 was important to the layout and definition of a diagram, the user could define userA to be equal to 5.1 and then use the userA constraint within the diagram definition. This would allow a single place to update the value across the entire diagram definition.
    - w – specifies the width
    - wArH – specifies the width of an arrowhead
    - wOff – specifies the amount of width offset

#### L.4.15.6.1.6 Constraint Relationships

=== "中文"

    The simple type ST_ConstraintRelationship defines the application of retrieval data the constraint is applied to. The following relationships are available:

    - self – the constraint is applicable to the current point
    - ch – the constraint is applicable to a child of the current point
    - des – the constraint is applicable to a descendant of the current point

=== "英文"

    **Constraint Relationships**

    The simple type ST_ConstraintRelationship defines the application of retrieval data the constraint is applied to. The following relationships are available:

    - self – the constraint is applicable to the current point
    - ch – the constraint is applicable to a child of the current point
    - des – the constraint is applicable to a descendant of the current point

#### L.4.15.6.1.7 Type of Element

=== "中文"

    The simple type ST_ElementType defines the type of element, or point which get created and how they are created from the data at hand. The different ways to pull from the data to create points are as follows:

    - all – use all of the data points, nodes and transitions
    - doc – use the document level, or root data point
    - node – use only data nodes input by the user
    - norm – in place for extensibility and behaves exactly opposite of the asst element
    - nonNorm – in place for extensibility and behaves exactly opposite of the nonAsst element
    - asst – use assistant data nodes within hierarchy algorithm
    - nonAsst – use non-assistant nodes within the hierarchy algorithm
    - parTrans – Use only parent transitions between nodes. Parent transitions are similar to sibling transitions, except that they represent parent/child relationships. Parent transitions are most commonly used in hierarchy diagrams, such as organization charts, to draw lines between parent and child nodes.
    - pres – specifies that the node is related to the presentation level
    - sibTrans – Use only sibling transitions between data nodes. These transitions represent sibling relationships between nodes, and are frequently mapped to arrows between shapes in the drawing. A sibTrans value is sometimes used to create white space between nodes.

=== "英文"

    **Type of Element**

    The simple type ST_ElementType defines the type of element, or point which get created and how they are created from the data at hand. The different ways to pull from the data to create points are as follows:

    - all – use all of the data points, nodes and transitions
    - doc – use the document level, or root data point
    - node – use only data nodes input by the user
    - norm – in place for extensibility and behaves exactly opposite of the asst element
    - nonNorm – in place for extensibility and behaves exactly opposite of the nonAsst element
    - asst – use assistant data nodes within hierarchy algorithm
    - nonAsst – use non-assistant nodes within the hierarchy algorithm
    - parTrans – Use only parent transitions between nodes. Parent transitions are similar to sibling transitions, except that they represent parent/child relationships. Parent transitions are most commonly used in hierarchy diagrams, such as organization charts, to draw lines between parent and child nodes.
    - pres – specifies that the node is related to the presentation level
    - sibTrans – Use only sibling transitions between data nodes. These transitions represent sibling relationships between nodes, and are frequently mapped to arrows between shapes in the drawing. A sibTrans value is sometimes used to create white space between nodes.

#### L.4.15.6.1.8 Parameter ID

=== "中文"

    The simple type ST_ParameterId defines parameters that can be used to modify the behavior or algorithms. The modifications are as follows:

    - horzAlign – specifies the horizontal alignment
    - vertAlign – specifies the vertical alignment
    - chDir – specifies the child direction
    - chAlign – specifies the alignment of the children
    - secChAlign – specifies a secondary child alignment
    - linDir – specifies whether children are arranged from left to right, right to left, top to bottom, or bottom to top
    - secLinDir – specifies a secondary linear direction in which children are
    - arranged from left to right, right to left, top to bottom, or bottom to top
    - stElem – specifies the point type of the layout node to use as the first shape in the cycle
    - bendPt – specifies where the bend point is to be located on connectors
    - connRout – specifies whether the connector is drawn as a single straight line, orthogonal lines with a single bend, or a curve that uses the diam constraint
    - begSty – specifies whether the beginning of the connector has an arrowhead
    - endSty – specifies whether the end of the connector has an arrowhead
    - dim – specifies the connector dimension, 2-D, 3-D, or custom
    - rotPath - if rotPath=alongPath, the algorithm rotates all children perpendicular to the line from the cycle’s center to the child node; otherwise they are not rotated. The alongPath value does not take rotation into account when determining if shapes overlap
    - ctrShpMap - None specifies to place nodes around a circle. First node (fNode) specifies to place the first node in the center and the remaining nodes around the circle
    - nodeHorzAlign – specifies the horizontal node alignment
    - nodeVertAlign – specifies the vertical node alignment
    - fallback – specifies if the fallback occurs in a single dimension (e.g. vertically) or if it occurs in two dimensions
    - txDir – specifies where the text of the first node starts
    - pyraAcctPos – specifies the placement of the fly-out grandchildren
    - pyraAcctTxMar – specifies the placement of one edge of the child text
    - txBlDir – Specifies the text block direction, vertical or horizontal
    - txAnchorHorz – Specifies the horizontal text anchor position.
    - txAnchorVert – Specifies the vertical text anchor position.
    - txAnchorHorzCh – Specifies the horizontal text anchor position for child text.
    - txAnchorVertCh – Specifies the vertical text anchor position for child text.
    - parTxLTRAlign – Specifies the paragraph alignment of parent text when the shape has only parent text. This parameter applies when the text direction is left to right.
    - partTxRTLAlign – Specifies the paragraph alignment of parent text when the shape has only parent text. This parameter applies when the text direction is right to left.
    - shpTxLTRAlignCh – Specifies the paragraph alignment of all text within the shape when the shape contains both parent and child text. This parameter applies when the text direction is left to right.
    - shpTxRTLAlignCh – Specifies the paragraph alignment of all text within the shape when the shape contains both parent and child text. This parameter applies when the text direction isright to left.
    - autoTxRot – specifies how text is oriented relative to the shape
    - grDir – Specifies the direction of growth for the snake algorithm.
    - flowDir – specifies weather nodes are arranged in rows or columns for the snake algorithm.
    - contDir – Specifies the direction of subsequent rows or columns in the snake algorithm.
    - bkpt – specifies the point at which the diagram starts to snake
    - off – specifies whether each row and column is centered or offset from the previous row or column
    - hierAlign – specifies the alignment of the hierarchy
    - bkPtFixedVal – specifies where the sname should break if bkpt is set to fixed
    - stBulletLvl – Specifies the level at which to start using bullets for incoming text.
    - stAng – Specifies the angle at which the first shape is placed. Angles are in degrees, measured clockwise from a line pointing straight upward from the center of the cycle.
    - spanAng – Specifies the angle the cycle spans. Final shapealign text is placed at stAng+spanAng, unless spanAng=360. In that case, the algorithm places the text so that shapes do not overlap
    - ar – Specifies the aspect ratio (width to height) of the composite node to use when determining child constraints. A value of 0 means leave the width and height constraints as is. The algorithm can temporarily shrink one dimension to achieve that ratio
    - lnSpPar – specifies the line spacing of the parent
    - lnSpAfParP – specifies the line spacing after the parent paragraph
    - LnSpCh specifies the line spacing of a child
    - lnSpAfChP – specifies the line spacing after the child paragraph
    - rtShortDist – Specifies the routing to use the shortest distance for connectors.
    - alignTx – specifies if to hold text or not
    - pyraLvlNode – If pyramid has a composite child node, specifies the name of the node that is a child of the composite that makes up the pyramid itself. If the node specifies a trapezoid shape, it modifies the adjustment handles to construct a pyramid.
    - pyraAcctBkgdNode – If pyramid has a composite child node, specifies the child node that should hold the child text.
    - pyraAcctTxNode – If pyramid has a composite child node, specifies the name of the node that is a child of the composite that makes up the child flyout shape.
    - srcNode – Specifies the name of the layout node from which to start the connection.
    - dstNode – Specifies the name of the layout node from which to end the connection from.
    - begPts – Specifies the point type for the beginning of a connector.
    - endPts – Specifies the point type for the end of a connector.
    - unknown – An unkown parameter id. This can be used by implementing applications to define a parameter id outside of the scope of what is defined by this simple type.

=== "英文"

    **Parameter ID**

    The simple type ST_ParameterId defines parameters that can be used to modify the behavior or algorithms. The modifications are as follows:

    - horzAlign – specifies the horizontal alignment
    - vertAlign – specifies the vertical alignment
    - chDir – specifies the child direction
    - chAlign – specifies the alignment of the children
    - secChAlign – specifies a secondary child alignment
    - linDir – specifies whether children are arranged from left to right, right to left, top to bottom, or bottom to top
    - secLinDir – specifies a secondary linear direction in which children are
    - arranged from left to right, right to left, top to bottom, or bottom to top
    - stElem – specifies the point type of the layout node to use as the first shape in the cycle
    - bendPt – specifies where the bend point is to be located on connectors
    - connRout – specifies whether the connector is drawn as a single straight line, orthogonal lines with a single bend, or a curve that uses the diam constraint
    - begSty – specifies whether the beginning of the connector has an arrowhead
    - endSty – specifies whether the end of the connector has an arrowhead
    - dim – specifies the connector dimension, 2-D, 3-D, or custom
    - rotPath - if rotPath=alongPath, the algorithm rotates all children perpendicular to the line from the cycle’s center to the child node; otherwise they are not rotated. The alongPath value does not take rotation into account when determining if shapes overlap
    - ctrShpMap - None specifies to place nodes around a circle. First node (fNode) specifies to place the first node in the center and the remaining nodes around the circle
    - nodeHorzAlign – specifies the horizontal node alignment
    - nodeVertAlign – specifies the vertical node alignment
    - fallback – specifies if the fallback occurs in a single dimension (e.g. vertically) or if it occurs in two dimensions
    - txDir – specifies where the text of the first node starts
    - pyraAcctPos – specifies the placement of the fly-out grandchildren
    - pyraAcctTxMar – specifies the placement of one edge of the child text
    - txBlDir – Specifies the text block direction, vertical or horizontal
    - txAnchorHorz – Specifies the horizontal text anchor position.
    - txAnchorVert – Specifies the vertical text anchor position.
    - txAnchorHorzCh – Specifies the horizontal text anchor position for child text.
    - txAnchorVertCh – Specifies the vertical text anchor position for child text.
    - parTxLTRAlign – Specifies the paragraph alignment of parent text when the shape has only parent text. This parameter applies when the text direction is left to right.
    - partTxRTLAlign – Specifies the paragraph alignment of parent text when the shape has only parent text. This parameter applies when the text direction is right to left.
    - shpTxLTRAlignCh – Specifies the paragraph alignment of all text within the shape when the shape contains both parent and child text. This parameter applies when the text direction is left to right.
    - shpTxRTLAlignCh – Specifies the paragraph alignment of all text within the shape when the shape contains both parent and child text. This parameter applies when the text direction isright to left.
    - autoTxRot – specifies how text is oriented relative to the shape
    - grDir – Specifies the direction of growth for the snake algorithm.
    - flowDir – specifies weather nodes are arranged in rows or columns for the snake algorithm.
    - contDir – Specifies the direction of subsequent rows or columns in the snake algorithm.
    - bkpt – specifies the point at which the diagram starts to snake
    - off – specifies whether each row and column is centered or offset from the previous row or column
    - hierAlign – specifies the alignment of the hierarchy
    - bkPtFixedVal – specifies where the sname should break if bkpt is set to fixed
    - stBulletLvl – Specifies the level at which to start using bullets for incoming text.
    - stAng – Specifies the angle at which the first shape is placed. Angles are in degrees, measured clockwise from a line pointing straight upward from the center of the cycle.
    - spanAng – Specifies the angle the cycle spans. Final shapealign text is placed at stAng+spanAng, unless spanAng=360. In that case, the algorithm places the text so that shapes do not overlap
    - ar – Specifies the aspect ratio (width to height) of the composite node to use when determining child constraints. A value of 0 means leave the width and height constraints as is. The algorithm can temporarily shrink one dimension to achieve that ratio
    - lnSpPar – specifies the line spacing of the parent
    - lnSpAfParP – specifies the line spacing after the parent paragraph
    - LnSpCh specifies the line spacing of a child
    - lnSpAfChP – specifies the line spacing after the child paragraph
    - rtShortDist – Specifies the routing to use the shortest distance for connectors.
    - alignTx – specifies if to hold text or not
    - pyraLvlNode – If pyramid has a composite child node, specifies the name of the node that is a child of the composite that makes up the pyramid itself. If the node specifies a trapezoid shape, it modifies the adjustment handles to construct a pyramid.
    - pyraAcctBkgdNode – If pyramid has a composite child node, specifies the child node that should hold the child text.
    - pyraAcctTxNode – If pyramid has a composite child node, specifies the name of the node that is a child of the composite that makes up the child flyout shape.
    - srcNode – Specifies the name of the layout node from which to start the connection.
    - dstNode – Specifies the name of the layout node from which to end the connection from.
    - begPts – Specifies the point type for the beginning of a connector.
    - endPts – Specifies the point type for the end of a connector.
    - unknown – An unkown parameter id. This can be used by implementing applications to define a parameter id outside of the scope of what is defined by this simple type.

#### L.4.15.6.1.9 Function Type

=== "中文"

    The simple type ST_FunctionType defines different types of conditional expressions that can be utilized. The different types of expressions are:

    - cnt – Specifies the count of items.
    - pos - Retrieves the position of the node in the specified set of nodes.
    - revPos - Reverse position function.
    - posEven - Returns 1 if the specified node is at an even numbered position in the data model.
    - posOdd - Returns 1 if the specified node is in an odd position in the data model.
    - var - Used to reference a variable.
    - depth - Specifies the depth of items.
    - maxDepth - Defines the maximum depth of items.

=== "英文"

    **Function Type**

    The simple type ST_FunctionType defines different types of conditional expressions that can be utilized. The different types of expressions are:

    - cnt – Specifies the count of items.
    - pos - Retrieves the position of the node in the specified set of nodes.
    - revPos - Reverse position function.
    - posEven - Returns 1 if the specified node is at an even numbered position in the data model.
    - posOdd - Returns 1 if the specified node is in an odd position in the data model.
    - var - Used to reference a variable.
    - depth - Specifies the depth of items.
    - maxDepth - Defines the maximum depth of items.

#### L.4.15.6.1.10 Function Operator

=== "中文"

    The simple type ST_FunctionOperator defines the different condition expression operators that can be used. The different operators are as follows:

    - equ – equal
    - neq – not equal
    - gt – greater than
    - lt – less than
    - gte – greater than or equal to
    - lte – less than or equal to

=== "英文"

    **Function Operator**

    The simple type ST_FunctionOperator defines the different condition expression operators that can be used. The different operators are as follows:

    - equ – equal
    - neq – not equal
    - gt – greater than
    - lt – less than
    - gte – greater than or equal to
    - lte – less than or equal to

#### L.4.15.6.1.11 Horizontal Alignment

=== "中文"

    The simple type, ST_DiagramHorizontalAlignment, specifies the different options available for alignment horizontally. The options are:
    
    - l – left
    - ctr – center
    - r – right
    - none – none 

=== "英文"

    **Horizontal Alignment**

    The simple type, ST_DiagramHorizontalAlignment, specifies the different options available for alignment horizontally. The options are:
    
    - l – left
    - ctr – center
    - r – right
    - none – none 

#### L.4.15.6.1.12 Vertical Alignment

=== "中文"

    The simple type, ST_VerticalAlignment, specifies the different options available for alignment vertically. The options are:

    - t/top – top
    - mid/center – middle
    - b/bottom – bottom
    - none – none

=== "英文"

    **Vertical Alignment**

    The simple type, ST_VerticalAlignment, specifies the different options available for alignment vertically. The options are:

    - t/top – top
    - mid/center – middle
    - b/bottom – bottom
    - none – none

#### L.4.15.6.1.13 Child Direction

=== "中文"

    The simple type ST_ChildDirection is used to specify the direction the children are laid out. The different options are:

    - horz – horizontally
    - vert – vertically

=== "英文"

    **Child Direction**

    The simple type ST_ChildDirection is used to specify the direction the children are laid out. The different options are:

    - horz – horizontally
    - vert – vertically

#### L.4.15.6.1.14 Child Alignment

=== "中文"

    The simple type ST_ChildAlignment defines the alignment parameter types for children. The different alignment types are:

    - t – top
    - b – bottom
    - l – left
    - r – right

=== "英文"

    **Child Alignment**

    The simple type ST_ChildAlignment defines the alignment parameter types for children. The different alignment types are:

    - t – top
    - b – bottom
    - l – left
    - r – right

#### L.4.15.6.1.15 Secondary Child Alignment

=== "中文"

    The simple type ST_SecondaryChildAlignment defines secondary alignment parameter types for children. The simple type ST_ChildAlignment is mirrored here with the addition of the none type.

=== "英文"

    **Secondary Child Alignment**

    The simple type ST_SecondaryChildAlignment defines secondary alignment parameter types for children. The simple type ST_ChildAlignment is mirrored here with the addition of the none type.

#### L.4.15.6.1.16 Linear Direction

=== "中文"

    The simple type ST_LinearDirection defines the linear direction parameter types. The direction types are as follows:

    - fromL – from left
    - fromR – from right
    - fromT – from top
    - fromB – from bottom

=== "英文"

    **Linear Direction**

    The simple type ST_LinearDirection defines the linear direction parameter types. The direction types are as follows:

    - fromL – from left
    - fromR – from right
    - fromT – from top
    - fromB – from bottom

#### L.4.15.6.1.17 Secondary Linear Direction

=== "中文"

    The simple type ST_SecondaryLinearDirection defines a secondary linear direction parameter. This simple type mirrors exactly the simple type ST_LinearDirection with the addition of none.

=== "英文"

    **Secondary Linear Direction**

    The simple type ST_SecondaryLinearDirection defines a secondary linear direction parameter. This simple type mirrors exactly the simple type ST_LinearDirection with the addition of none.

#### L.4.15.6.1.18 Starting Element

=== "中文"

    The simple type ST_StartingElement specifies the first node point type for a cycle diagram. The different starting elements are:
    
    - node – node
    - trans – transition

=== "英文"

    **Starting Element**

    The simple type ST_StartingElement specifies the first node point type for a cycle diagram. The different starting elements are:
    
    - node – node
    - trans – transition

#### L.4.15.6.1.19 Rotation Path

=== "中文"

    The simple type ST_RotationPath specifies the way in which the algorithm rotates children. The different rotation types are:

    - none – no rotation is performed
    - alongPath – the children are rotated perpendicular to the line from the cycle’s center to the child node

=== "英文"

    **Rotation Path**

    The simple type ST_RotationPath specifies the way in which the algorithm rotates children. The different rotation types are:

    - none – no rotation is performed
    - alongPath – the children are rotated perpendicular to the line from the cycle’s center to the child node

#### L.4.15.6.1.20 Center Shape Mapping

=== "中文"

    The simple type ST_CenterShapeMapping specifies how the first node of a cycle diagram is laid out within the diagram. The different places to put the first node are:

    - none – the node is laid out around the circle
    - fNode – the node is placed in the center of the circle and the remaining nodes along the outside of the circle

=== "英文"

    **Center Shape Mapping**

    The simple type ST_CenterShapeMapping specifies how the first node of a cycle diagram is laid out within the diagram. The different places to put the first node are:

    - none – the node is laid out around the circle
    - fNode – the node is placed in the center of the circle and the remaining nodes along the outside of the circle

#### L.4.15.6.1.21 Bend Point

=== "中文"

    The simple type ST_BendPoint specifies where the bend point is to be located along elbow connectors. The different options are:

    - beg – beginning
    - def – default
    - end – end

=== "英文"

    **Bend Point**

    The simple type ST_BendPoint specifies where the bend point is to be located along elbow connectors. The different options are:

    - beg – beginning
    - def – default
    - end – end

#### L.4.15.6.1.22 Connector Routing

=== "中文"

    The simple type ST_ConnectorRouting defines how the routing of a connector happens within the diagram. The different routing options are:
    
    - stra – straight
    - bend – an elbow connection
    - curve – a curved connection
    - longCurve – a curved connection with a larger radius than simple curve

=== "英文"

    **nector Routing**

    The simple type ST_ConnectorRouting defines how the routing of a connector happens within the diagram. The different routing options are:
    
    - stra – straight
    - bend – an elbow connection
    - curve – a curved connection
    - longCurve – a curved connection with a larger radius than simple curve

#### L.4.15.6.1.23 Arrowhead Style

=== "中文"

    The simple type ST_ArrowheadStyle defines the style of the arrowhead used on a connector. The different options are:
    
    - auto – automatic
    - arr – an arrowhead is used
    - noArr – no arrowhead is used

=== "英文"

    **Arrowhead Style**

    The simple type ST_ArrowheadStyle defines the style of the arrowhead used on a connector. The different options are:
    
    - auto – automatic
    - arr – an arrowhead is used
    - noArr – no arrowhead is used

#### L.4.15.6.1.24 Connector Dimension

=== "中文"

    The simple type ST_ConnectorDimension defines the dimension of a connector used in a diagram. The different dimension types are:
    
    - 1D – a single dimension connector, for example, a line
    - 2D – a two dimensional connector, for example, an arrow
    - cust – custom

=== "英文"

    **Connector Dimension**

    The simple type ST_ConnectorDimension defines the dimension of a connector used in a diagram. The different dimension types are:
    
    - 1D – a single dimension connector, for example, a line
    - 2D – a two dimensional connector, for example, an arrow
    - cust – custom

#### L.4.15.6.1.25 Connector Point

=== "中文"

    The simple type ST_ConnectorPoint defines the point at which the connector starts and ends. The different beginning and ending types are:

    - auto – automatic
    - bCtr – bottom center
    - ctr – center
    - midL – middle left
    - midR – middle right
    - tCtr – top center
    - bL – bottom left
    - bR – bottom right
    - tL – top left
    - tR – top right
    - radial – radial

=== "英文"

    **Connector Point**

    The simple type ST_ConnectorPoint defines the point at which the connector starts and ends. The different beginning and ending types are:

    - auto – automatic
    - bCtr – bottom center
    - ctr – center
    - midL – middle left
    - midR – middle right
    - tCtr – top center
    - bL – bottom left
    - bR – bottom right
    - tL – top left
    - tR – top right
    - radial – radial

#### L.4.15.6.1.26 Node Horizontal Alignment

=== "中文"

    The simple type ST_NodeHorizontalAlignment defines the alignment of a node in the horizontal direction. The different alignments are:
    
    - l – left
    - ctr – center
    - r – right

=== "英文"

    **Node Horizontal Alignment**

    The simple type ST_NodeHorizontalAlignment defines the alignment of a node in the horizontal direction. The different alignments are:
    
    - l – left
    - ctr – center
    - r – right

#### L.4.15.6.1.27 Node Vertical Alignment

=== "中文"

    The simple type ST_NodeVerticalAlignment defines the alignment of a node in the vertical direction. The different alignments are:

    - t – top
    - mid – mid
    - b – bottom

=== "英文"

    **Node Vertical Alignment**

    The simple type ST_NodeVerticalAlignment defines the alignment of a node in the vertical direction. The different alignments are:

    - t – top
    - mid – mid
    - b – bottom

#### L.4.15.6.1.28 Fallback Dimension

=== "中文"

    The simple type ST_FallbackDimension defines the number of dimensions to be used if fallback causes the diagram to be resized. The different options are:

    - 1D – fallback occurs in a single dimension (X or Y)
    - 2D – fallback occurs in two dimensions (X and Y)

=== "英文"

    **Fallback Dimension**

    The simple type ST_FallbackDimension defines the number of dimensions to be used if fallback causes the diagram to be resized. The different options are:

    - 1D – fallback occurs in a single dimension (X or Y)
    - 2D – fallback occurs in two dimensions (X and Y)

#### L.4.15.6.1.29 Text Direction

=== "中文"

    The simple type ST_TextDirection specifies where the text on the first node starts. The different text directions are:
    
    - fromT – from top
    - fromB – from bottom

=== "英文"

    **Text Direction**

    The simple type ST_TextDirection specifies where the text on the first node starts. The different text directions are:
    
    - fromT – from top
    - fromB – from bottom

#### L.4.15.6.1.30 Pyramid Accent Position

=== "中文"

    The simple type ST_PyramidAccentPosition defines where the position of the fly-out grandchildren. The possible positions are:
    
    - bef – before
    - after – after

=== "英文"

    **Pyramid Accent Position**

    The simple type ST_PyramidAccentPosition defines where the position of the fly-out grandchildren. The possible positions are:
    
    - bef – before
    - after – after

#### L.4.15.6.1.31 Pyramid Text Margin

=== "中文"

    The simple type ST_PyramidAccentTextMargin specifies the alignment of the text in the fly-out grandchildren. The different alignments are:

    - step – the text is against the edge of the pyramid
    - stack – the text aligns

=== "英文"

    **Pyramid Text Margin**

    The simple type ST_PyramidAccentTextMargin specifies the alignment of the text in the fly-out grandchildren. The different alignments are:

    - step – the text is against the edge of the pyramid
    - stack – the text aligns

#### L.4.15.6.1.32 Text Block Direction

=== "中文"

    The simple type ST_TextBlockDirection defines the text block direction. The different direction the text can have are:

    - vert – vertical
    - horz – horizontal

=== "英文"

    **Text Block Direction**

    The simple type ST_TextBlockDirection defines the text block direction. The different direction the text can have are:

    - vert – vertical
    - horz – horizontal

#### L.4.15.6.1.33 Text Anchor Horizontal

=== "中文"

    The simple type ST_AnchorHorizontal is responsible for anchoring text horizontally. The available options are:

    - none – no anchor set
    - ctr – the text is anchored the center

=== "英文"

    **Text Anchor Horizontal**

    The simple type ST_AnchorHorizontal is responsible for anchoring text horizontally. The available options are:

    - none – no anchor set
    - ctr – the text is anchored the center

#### L.4.15.6.1.34 Text Anchor Vertical

=== "中文"

    The simple type ST_AnchorVertical is responsible for anchoring the text vertically. The available options are:

    - t – top anchor
    - mid – middle anchor
    - b – bottom anchor

=== "英文"

    **Text Anchor Vertical**

    The simple type ST_AnchorVertical is responsible for anchoring the text vertically. The available options are:

    - t – top anchor
    - mid – middle anchor
    - b – bottom anchor

#### L.4.15.6.1.35 Text Alignment

=== "中文"

    The simple type ST_TextAlignment defines the text alignment. The available options are:

    - l – left
    - ctr – ctr
    - r – right

=== "英文"

    **Text Alignment**

    The simple type ST_TextAlignment defines the text alignment. The available options are:

    - l – left
    - ctr – ctr
    - r – right

#### L.4.15.6.1.36 Auto Text Rotation

=== "中文"

    The simple type ST_AutoTextRotation defines the behavior of the text as the containing shape is rotated. The following options are available:
    
    - none – no rotation, the text rotates with the shape
    - upr – upright
    - grav – gravity

=== "英文"

    **Auto Text Rotation**

    The simple type ST_AutoTextRotation defines the behavior of the text as the containing shape is rotated. The following options are available:
    
    - none – no rotation, the text rotates with the shape
    - upr – upright
    - grav – gravity

#### L.4.15.6.1.37 Grow Direction

=== "中文"

    The simple type ST_GrowDirection defines the growing behavior of the snake algorithm. The following options are available:
    
    - tL – grow from the top left
    - tR – grow from the top right
    - bL – grow from the bottom left
    - gR – grow from the bottom right

=== "英文"

    **Grow Direction**

    The simple type ST_GrowDirection defines the growing behavior of the snake algorithm. The following options are available:
    
    - tL – grow from the top left
    - tR – grow from the top right
    - bL – grow from the bottom left
    - gR – grow from the bottom right

#### L.4.15.6.1.38 Flow Direction

=== "中文"

    The simple type ST_FlowDirection Specifies whether nodes are arranged in rows or columns for the snake algorithm. The following options are available:

    - row – Row
    - col – column

=== "英文"

    **Flow Direction**

    The simple type ST_FlowDirection Specifies whether nodes are arranged in rows or columns for the snake algorithm. The following options are available:

    - row – Row
    - col – column

#### L.4.15.6.1.39 Continue Direction

=== "中文"

    The simple type ST_ContinueDirection specifies the direction of the subsequent row or column in the snake algorithm. The following options are available:
    
    - revDir – reverse direction
    - sameDir – same direction

=== "英文"

    **Continue Direction**

    The simple type ST_ContinueDirection specifies the direction of the subsequent row or column in the snake algorithm. The following options are available:
    
    - revDir – reverse direction
    - sameDir – same direction

#### L.4.15.6.1.40 Breakpoint

=== "中文"

=== "英文"

    **Breakpoint**

    The simple type ST_Breakpoint defines the behavior of a snake diagram’s breaking behavior. The available options are:

    - endCnv – end of canvas
    - bal – balanced
    - fixed – fixed

#### L.4.15.6.1.41 Offset

=== "中文"

    The simple type ST_Offset defines the behavior of whether each row or column in the snake algorithm is offset from the previous row or column. The available options are:

    - ctr – the offset is center based
    - off – there is an offset defined

=== "英文"

    **Offset**

    The simple type ST_Offset defines the behavior of whether each row or column in the snake algorithm is offset from the previous row or column. The available options are:

    - ctr – the offset is center based
    - off – there is an offset defined

#### L.4.15.6.1.42 Hierarchy Alignment

=== "中文"

    The simple type ST_HierarchyAlignment specifies the relationship between parent and children in a hierarchy diagram. The following options exist:

    - tL – top left
    - tR – top right
    - tCtrCh – top center children
    - tCtrDes – top center descendants
    - bL – bottom left
    - bR – bottom right
    - bCtrCh – bottom center children
    - bCtrDes – bottom center descendants
    - lT – left top
    - lB – left bottom
    - lCtrCh – left center children
    - lCtrDes – left center descendants
    - rT – right top
    - rB – right bottom
    - rCtrCh – right center children
    - rCtrDes – right center descendants

=== "英文"

    **Hierarchy Alignment**

    The simple type ST_HierarchyAlignment specifies the relationship between parent and children in a hierarchy diagram. The following options exist:

    - tL – top left
    - tR – top right
    - tCtrCh – top center children
    - tCtrDes – top center descendants
    - bL – bottom left
    - bR – bottom right
    - bCtrCh – bottom center children
    - bCtrDes – bottom center descendants
    - lT – left top
    - lB – left bottom
    - lCtrCh – left center children
    - lCtrDes – left center descendants
    - rT – right top
    - rB – right bottom
    - rCtrCh – right center children
    - rCtrDes – right center descendants

### L.4.15.6.2 Variable Type

=== "中文"

    The simple type ST_VariableType defines the type of the conditional expression. These variables turn user interface options on and off. The available variable types are:

    - unknown – Unknown variable type. This can be used by implementing applications to define a variable type outside of the scope of what is defined by this simple type.
    - orgChart – organizational chart command
    - chMax – used for the insert shape dropdown commands
    - chPref – used for the insert shape button
    - bulEnabled – used for the insert bullet command
    - dir – diagram direction, RTL or LTR
    - hierBranch – stores the different layouts for org chart
    - animOne – exposes options for animation
    - animLvl – exposes options for animation

=== "英文"

    **Variable Type**

    The simple type ST_VariableType defines the type of the conditional expression. These variables turn user interface options on and off. The available variable types are:

    - unknown – Unknown variable type. This can be used by implementing applications to define a variable type outside of the scope of what is defined by this simple type.
    - orgChart – organizational chart command
    - chMax – used for the insert shape dropdown commands
    - chPref – used for the insert shape button
    - bulEnabled – used for the insert bullet command
    - dir – diagram direction, RTL or LTR
    - hierBranch – stores the different layouts for org chart
    - animOne – exposes options for animation
    - animLvl – exposes options for animation

#### L.4.15.6.2.1 Output Shape Type

=== "中文"

    The simple type ST_OutputShapeType defines special shape types which are unique to diagrams. The unique shape types are:
    
    - none – none
    - conn – connector

=== "英文"

    **Output Shape Type**

    The simple type ST_OutputShapeType defines special shape types which are unique to diagrams. The unique shape types are:
    
    - none – none
    - conn – connector

### L.4.15.6.3 Diagram Definitions

=== "中文"

    Diagram definitions define the look of a diagram. They utilize almost all the aspects of the file format discussed thus far in order to create layout properties which get translated into visual diagrams.

    There are a few more simple types that need to be defined before talking about the larger aspects of what it takes to create a diagram definition. Many of these simple types are provided as wrappers or lists of the above mentioned simple types.

=== "英文"

    **Diagram Definitions**

    Diagram definitions define the look of a diagram. They utilize almost all the aspects of the file format discussed thus far in order to create layout properties which get translated into visual diagrams.

    There are a few more simple types that need to be defined before talking about the larger aspects of what it takes to create a diagram definition. Many of these simple types are provided as wrappers or lists of the above mentioned simple types.

#### L.4.15.6.3.1 Lists

=== "中文"

    There are a group of simple types which act as lists of the simple types already mentioned. They are all defined in the following general way:

    ```xml
    <xsd:simpleType name= "NAME OF TYPE" >
        <xsd:list itemType= "NAME OF SIMPLE TYPE" />
    </xsd:simpleType>
    ```

    The list of these list types are the following simple types:

    - ST_AxisTypes – list of ST_AxisType
    - ST_ElementTypes – list of ST_ElementType
    - ST_Ints – list of xsd:int
    - ST_UnsignedInts – list of xsd:unsignedInt
    - ST_Booleans – list of xsd:boolean

=== "英文"

    **Lists**

    There are a group of simple types which act as lists of the simple types already mentioned. They are all defined in the following general way:

    ```xml
    <xsd:simpleType name= "NAME OF TYPE" >
        <xsd:list itemType= "NAME OF SIMPLE TYPE" />
    </xsd:simpleType>
    ```

    The list of these list types are the following simple types:

    - ST_AxisTypes – list of ST_AxisType
    - ST_ElementTypes – list of ST_ElementType
    - ST_Ints – list of xsd:int
    - ST_UnsignedInts – list of xsd:unsignedInt
    - ST_Booleans – list of xsd:boolean

#### L.4.15.6.3.2 Function Value

=== "中文"

    The simple type ST_FunctionValue is a value for a condition expression. It is defined as:

    ```xml
    <xsd:simpleType name="ST_FunctionValue" final="restriction">
        <xsd:union memberTypes="xsd:int xsd:boolean ST_Direction ST_HierBranchStyle ST_AnimOneStr ST_AnimLvlStr" />
    </xsd:simpleType>
    ```

=== "英文"

    **Function Value**

    The simple type ST_FunctionValue is a value for a condition expression. It is defined as:

    ```xml
    <xsd:simpleType name="ST_FunctionValue" final="restriction">
        <xsd:union memberTypes="xsd:int xsd:boolean ST_Direction ST_HierBranchStyle ST_AnimOneStr ST_AnimLvlStr" />
    </xsd:simpleType>
    ```

#### L.4.15.6.3.3 Direction

=== "中文"

    The simple type ST_Direction defines the direction the diagram is to be laid out. The directions available are:

    - norm – normal
    - rev – reversed

=== "英文"

    **Direction**

    The simple type ST_Direction defines the direction the diagram is to be laid out. The directions available are:

    - norm – normal
    - rev – reversed

#### L.4.15.6.3.4 Hierarchy Branch Style

=== "中文"

    The simple type ST_HierBranchStyle changes the behavior of the branch style in hierarchy, or org chart, diagrams. This value can be modified by a user directly from the user interface. The different types of branch styles are:

    - l – left
    - r – right
    - hang – hanging
    - std – standard
    - init – initial

=== "英文"

    **Hierarchy Branch Style**

    The simple type ST_HierBranchStyle changes the behavior of the branch style in hierarchy, or org chart, diagrams. This value can be modified by a user directly from the user interface. The different types of branch styles are:

    - l – left
    - r – right
    - hang – hanging
    - std – standard
    - init – initial

#### L.4.15.6.3.5 One by One Animation

=== "中文"

    The simple type ST_AnimOneStr allows for differentiation in the way a one-by-one animation is displayed in the user interface. The following options are available:

    - none – nothing is displayed
    - one – the term one-by-one is used
    - branch – the term branch one-by-one is used to distinguish a hierarchy diagram

=== "英文"

    **One by One Animation**

    The simple type ST_AnimOneStr allows for differentiation in the way a one-by-one animation is displayed in the user interface. The following options are available:

    - none – nothing is displayed
    - one – the term one-by-one is used
    - branch – the term branch one-by-one is used to distinguish a hierarchy diagram

#### L.4.15.6.3.6 Level Animation

=== "中文"

    The simple type ST_AnimLvlStr acts very much like the simple type ST_AminOneStr, as it allows for two different descriptions of a single animation depending upon the desired behavior for a particular diagram. The following allows for differentiation of radial diagrams. The different options are:

    - none – nothing
    - lvl – normal depth first traversal
    - ctr – allows a radial diagram to be shown with the center node first

=== "英文"

    **Level Animation**

    The simple type ST_AnimLvlStr acts very much like the simple type ST_AminOneStr, as it allows for two different descriptions of a single animation depending upon the desired behavior for a particular diagram. The following allows for differentiation of radial diagrams. The different options are:

    - none – nothing
    - lvl – normal depth first traversal
    - ctr – allows a radial diagram to be shown with the center node first

#### L.4.15.6.3.7 Org Chart Flag

=== "中文"

    The complex type CT_OrgChart defines that the diagram is an organizational chart. Organizational charts contain special behavior in that assistants can now be utilized correctly. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_OrgChart">
        <xsd:attribute name="val" type="xsd:boolean" default="false" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Org Chart Flag**

    The complex type CT_OrgChart defines that the diagram is an organizational chart. Organizational charts contain special behavior in that assistants can now be utilized correctly. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_OrgChart">
        <xsd:attribute name="val" type="xsd:boolean" default="false" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.8 Node Count

=== "中文"

    The simple type ST_NodeCount holds a value that is used by the complex types CT_ChildMax and CT_ChildPref.

=== "英文"

    **Node Count**

    The simple type ST_NodeCount holds a value that is used by the complex types CT_ChildMax and CT_ChildPref.

#### L.4.15.6.3.9 Child Max

=== "中文"

    This complex type defines when the user interface for inserting a child shape is to become disabled for a given node, or rather the max number of children that the user interface is enabled for. This complex type is defined as:

    ```xml
    <xsd:complexType name="CT_ChildMax">
        <xsd:attribute name="val" type="ST_NodeCount" default="-1" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Child Max**

    This complex type defines when the user interface for inserting a child shape is to become disabled for a given node, or rather the max number of children that the user interface is enabled for. This complex type is defined as:

    ```xml
    <xsd:complexType name="CT_ChildMax">
        <xsd:attribute name="val" type="ST_NodeCount" default="-1" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.10 Child Preference

=== "中文"

    This complex type defines how many children are inserted with a single action through the user interface to add a child. This is useful in hierarchy diagrams in which one would like to specify that every shape should have three children. A single click of the add shape button would add three children. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_ChildPref">
        <xsd:attribute name="val" type="ST_NodeCount" default="-1" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Child Preference**

    This complex type defines how many children are inserted with a single action through the user interface to add a child. This is useful in hierarchy diagrams in which one would like to specify that every shape should have three children. A single click of the add shape button would add three children. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_ChildPref">
        <xsd:attribute name="val" type="ST_NodeCount" default="-1" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.11 Bullets Enabled

=== "中文"

    This complex type defines if the user interface for inserting a bullet into a shape is enabled or disabled for a given node. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_BulletEnabled">
        <xsd:attribute name="val" type="xsd:boolean" default="false" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Bullets Enabled**

    This complex type defines if the user interface for inserting a bullet into a shape is enabled or disabled for a given node. The complex type is defined as follows:

    ```xml
    <xsd:complexType name="CT_BulletEnabled">
        <xsd:attribute name="val" type="xsd:boolean" default="false" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.12 Direction

=== "中文"

    This complex type defines the direction of the diagram, be it normal or reversed. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Direction">
        <xsd:attribute name="val" type="ST_Direction" default="norm" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Direction**

    This complex type defines the direction of the diagram, be it normal or reversed. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Direction">
        <xsd:attribute name="val" type="ST_Direction" default="norm" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.13 Hierarchy Branch Style

=== "中文"

    This complex type defines the hierarchy branch style for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_HierBranchStyle">
        <xsd:attribute name="val" type="ST_HierBranchStyle" default="std" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Hierarchy Branch Style**

    This complex type defines the hierarchy branch style for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_HierBranchStyle">
        <xsd:attribute name="val" type="ST_HierBranchStyle" default="std" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.14 Animate as One

=== "中文"

    This complex type defines the animate as one value for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_AnimOne">
        <xsd:attribute name="val" type="ST_AnimOneStr" default="one" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Animate as One**

    This complex type defines the animate as one value for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_AnimOne">
        <xsd:attribute name="val" type="ST_AnimOneStr" default="one" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.15 Animate by Level

=== "中文"

    This complex type defines the animate by level value for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_AnimLvl">
        <xsd:attribute name="val" type="ST_AnimLvlStr" default="none" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Animate by Level**

    This complex type defines the animate by level value for a diagram. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_AnimLvl">
        <xsd:attribute name="val" type="ST_AnimLvlStr" default="none" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.16 Layout Property Set

=== "中文"

    The complex type CT_LayoutPropertySet holds all of the layout properties for a given diagram. The layout property set is a single structure which contains most of what has been talked about thus far in a diagram definition. The layout property set is defined as:

    ```xml
    <xsd:complexType name="CT_LayoutVariablePropertySet">
        <xsd:sequence>
            <xsd:element name="orgChart" type="CT_OrgChart" minOccurs="0" maxOccurs="1" />
            <xsd:element name="chMax" type="CT_ChildMax" minOccurs="0" maxOccurs="1" />
            <xsd:element name="chPref" type="CT_ChildPref" minOccurs="0" maxOccurs="1" />
            <xsd:element name="bulletEnabled" type="CT_BulletEnabled" minOccurs="0" maxOccurs="1" />
            <xsd:element name="dir" type="CT_Direction" minOccurs="0" maxOccurs="1" />
            <xsd:element name="hierBranch" type="CT_HierBranchStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="animOne" type="CT_AnimOne" minOccurs="0" maxOccurs="1" />
            <xsd:element name="animLvl" type="CT_AnimLvl" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    Because all of the contents of this complex type have already been discussed, no further detail on this complex type needs to be given.

=== "英文"

    **Layout Property Set**

    The complex type CT_LayoutPropertySet holds all of the layout properties for a given diagram. The layout property set is a single structure which contains most of what has been talked about thus far in a diagram definition. The layout property set is defined as:

    ```xml
    <xsd:complexType name="CT_LayoutVariablePropertySet">
        <xsd:sequence>
            <xsd:element name="orgChart" type="CT_OrgChart" minOccurs="0" maxOccurs="1" />
            <xsd:element name="chMax" type="CT_ChildMax" minOccurs="0" maxOccurs="1" />
            <xsd:element name="chPref" type="CT_ChildPref" minOccurs="0" maxOccurs="1" />
            <xsd:element name="bulletEnabled" type="CT_BulletEnabled" minOccurs="0" maxOccurs="1" />
            <xsd:element name="dir" type="CT_Direction" minOccurs="0" maxOccurs="1" />
            <xsd:element name="hierBranch" type="CT_HierBranchStyle" minOccurs="0" maxOccurs="1" />
            <xsd:element name="animOne" type="CT_AnimOne" minOccurs="0" maxOccurs="1" />
            <xsd:element name="animLvl" type="CT_AnimLvl" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
    </xsd:complexType>
    ```

    Because all of the contents of this complex type have already been discussed, no further detail on this complex type needs to be given.

#### L.4.15.6.3.17 Iterators

=== "中文"

    The attribute group AG_IteratorAttributes defines the attributes used by the iterators forEach, presOf, and if. The attribute group is defined as follows:

    ```xml
    <xsd:attributeGroup name="AG_IteratorAttributes">
        <xsd:attribute name="axis" type="ST_AxisTypes" use="optional" default="none" />
        <xsd:attribute name="ptType" type="ST_ElementTypes" use="optional" default="all" />
        <xsd:attribute name="hideLastTrans" type="ST_Booleans" use="optional" default="true" />
        <xsd:attribute name="st" type="ST_Ints" use="optional" default="1" />
        <xsd:attribute name="cnt" type="ST_UnsignedInts" use="optional" default="0" />
        <xsd:attribute name="step" type="ST_Ints" use="optional" default="1" />
    </xsd:attributeGroup>
    ```

=== "英文"

    **Iterators**

    The attribute group AG_IteratorAttributes defines the attributes used by the iterators forEach, presOf, and if. The attribute group is defined as follows:

    ```xml
    <xsd:attributeGroup name="AG_IteratorAttributes">
        <xsd:attribute name="axis" type="ST_AxisTypes" use="optional" default="none" />
        <xsd:attribute name="ptType" type="ST_ElementTypes" use="optional" default="all" />
        <xsd:attribute name="hideLastTrans" type="ST_Booleans" use="optional" default="true" />
        <xsd:attribute name="st" type="ST_Ints" use="optional" default="1" />
        <xsd:attribute name="cnt" type="ST_UnsignedInts" use="optional" default="0" />
        <xsd:attribute name="step" type="ST_Ints" use="optional" default="1" />
    </xsd:attributeGroup>
    ```

#### L.4.15.6.3.18 Constraints

=== "中文"

    The attribute group AG_ConstraintAttributes defines the attributes used to specify a constraint. The attribute group is defined as:

    ```xml
    <xsd:attributeGroup name="AG_ConstraintAttributes">
        <xsd:attribute name="type" type="ST_ConstraintType" use="required" />
        <xsd:attribute name="for" type="ST_ConstraintRelationship" use="optional" default="self" />
        <xsd:attribute name="forName" type="xsd:IDREF" use="optional" />
        <xsd:attribute name="ptType" type="ST_ElementType" use="optional" default="all" />
    </xsd:attributeGroup>
    ```

=== "英文"

    **Constraints**

    The attribute group AG_ConstraintAttributes defines the attributes used to specify a constraint. The attribute group is defined as:

    ```xml
    <xsd:attributeGroup name="AG_ConstraintAttributes">
        <xsd:attribute name="type" type="ST_ConstraintType" use="required" />
        <xsd:attribute name="for" type="ST_ConstraintRelationship" use="optional" default="self" />
        <xsd:attribute name="forName" type="xsd:IDREF" use="optional" />
        <xsd:attribute name="ptType" type="ST_ElementType" use="optional" default="all" />
    </xsd:attributeGroup>
    ```

#### L.4.15.6.3.19 Constraint References

=== "中文"

    The attribute group AG_ConstraintRefAttributes defines the attributes used to specify a constraint reference. The attribute group is defined as:

    ```xml
    <xsd:attributeGroup name="AG_ConstraintRefAttributes">
        <xsd:attribute name="refType" type="ST_ConstraintType" use="optional" default="unknown" />
        <xsd:attribute name="refFor" type="ST_ConstraintRelationship" use="optional" default="self" />
        <xsd:attribute name="refForName" type="xsd:IDREF" use="optional" />
        <xsd:attribute name="refPtType" type="ST_ElementType" use="optional" default="all" />
    </xsd:attributeGroup>
    ```

=== "英文"

    **Constraint References**

    The attribute group AG_ConstraintRefAttributes defines the attributes used to specify a constraint reference. The attribute group is defined as:

    ```xml
    <xsd:attributeGroup name="AG_ConstraintRefAttributes">
        <xsd:attribute name="refType" type="ST_ConstraintType" use="optional" default="unknown" />
        <xsd:attribute name="refFor" type="ST_ConstraintRelationship" use="optional" default="self" />
        <xsd:attribute name="refForName" type="xsd:IDREF" use="optional" />
        <xsd:attribute name="refPtType" type="ST_ElementType" use="optional" default="all" />
    </xsd:attributeGroup>
    ```

#### L.4.15.6.3.20 Constraint

=== "中文"

    The complex type CT_Constraint define a constraint within the layout framework. A constraint acts as a limit or sets a value to a given parameter in a diagram definition, for example, it can be used to specify that all nodes of a give point type are the same size. A constraint is defined as:

    ```xml
    <xsd:complexType name="CT_Constraint">
        <xsd:attributeGroup ref="AG_ConstraintAttributes" />
        <xsd:attributeGroup ref="AG_ConstraintRefAttributes" />
        <xsd:attribute name="op" type="ST_BoolOperator" use="optional" default="none" />
        <xsd:attribute name="val" type="xsd:double" use="optional" default="0" />
        <xsd:attribute name="fact" type="xsd:double" use="optional" default="1" />
    </xsd:complexType>
    ```

=== "英文"

    **Constraint**

    The complex type CT_Constraint define a constraint within the layout framework. A constraint acts as a limit or sets a value to a given parameter in a diagram definition, for example, it can be used to specify that all nodes of a give point type are the same size. A constraint is defined as:

    ```xml
    <xsd:complexType name="CT_Constraint">
        <xsd:attributeGroup ref="AG_ConstraintAttributes" />
        <xsd:attributeGroup ref="AG_ConstraintRefAttributes" />
        <xsd:attribute name="op" type="ST_BoolOperator" use="optional" default="none" />
        <xsd:attribute name="val" type="xsd:double" use="optional" default="0" />
        <xsd:attribute name="fact" type="xsd:double" use="optional" default="1" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.21 Constraint List

=== "中文"

    The complex type CT_Constraints is a sequence of CT_Constraint complex types. It is defined as:

    ```xml
    <xsd:complexType name="CT_Constraints">
        <xsd:sequence>
            <xsd:element name="constr" type="CT_Constraint" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Constraint List**

    The complex type CT_Constraints is a sequence of CT_Constraint complex types. It is defined as:

    ```xml
    <xsd:complexType name="CT_Constraints">
        <xsd:sequence>
            <xsd:element name="constr" type="CT_Constraint" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.6.3.22 Rule

=== "中文"

    The complex type CT_NumericRule defines a layout framework constraint rule. Rules are run after the diagram is created in order to specify what happens when the diagram doesn’t fully fit within the bounds. This allows for specific behavior to be defined rather than using default rules for fitting the diagram. A rule is defined in the following way:

    ```xml
    <xsd:complexType name="CT_NumericRule">
        <xsd:attributeGroup ref="AG_ConstraintAttributes" />
        <xsd:attribute name="val" type="xsd:double" use="optional" default="NaN" />
        <xsd:attribute name="fact" type="xsd:double" use="optional" default="NaN" />
        <xsd:attribute name="max" type="xsd:double" use="optional" default="NaN" />
    </xsd:complexType>
    ```

=== "英文"

    **Rule**

    The complex type CT_NumericRule defines a layout framework constraint rule. Rules are run after the diagram is created in order to specify what happens when the diagram doesn’t fully fit within the bounds. This allows for specific behavior to be defined rather than using default rules for fitting the diagram. A rule is defined in the following way:

    ```xml
    <xsd:complexType name="CT_NumericRule">
        <xsd:attributeGroup ref="AG_ConstraintAttributes" />
        <xsd:attribute name="val" type="xsd:double" use="optional" default="NaN" />
        <xsd:attribute name="fact" type="xsd:double" use="optional" default="NaN" />
        <xsd:attribute name="max" type="xsd:double" use="optional" default="NaN" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.23 Rule List

=== "中文"

    The complex type CT_Rules is simply a list of CT_NumericRule complex types. It is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Rules">
        <xsd:sequence>
            <xsd:element name="rule" type="CT_NumericRule" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Rule List**

    The complex type CT_Rules is simply a list of CT_NumericRule complex types. It is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Rules">
        <xsd:sequence>
            <xsd:element name="rule" type="CT_NumericRule" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.6.3.24 Presentation Of

=== "中文"

    The complex type CT_PresentationOf defines the mapping between data and the diagram. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_PresentationOf">
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
    </xsd:complexType>
    ```

=== "英文"

    **Presentation Of**

    The complex type CT_PresentationOf defines the mapping between data and the diagram. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_PresentationOf">
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.25 Layout Shape

=== "中文"

    The simple type ST_LayoutShapeType is a simple type that contains all of the shapes available which can be used within a diagram. The simple type is defined as a union of ST_OutputShapeType and an externally defined ST_ShapeType.

=== "英文"

    **Layout Shape**

    The simple type ST_LayoutShapeType is a simple type that contains all of the shapes available which can be used within a diagram. The simple type is defined as a union of ST_OutputShapeType and an externally defined ST_ShapeType.

#### L.4.15.6.3.26 Index1

=== "中文"

    The simple type ST_Index1 defines a 1-based index that is used to index values elsewhere. The simple type is defined as:

    ```xml
    <xsd:simpleType name="ST_Index1">
        <xsd:restriction base="xsd:unsignedInt">
            <xsd:minInclusive value="1" />
        </xsd:restriction>
    </xsd:simpleType>
    ```

=== "英文"

    **Index1**

    The simple type ST_Index1 defines a 1-based index that is used to index values elsewhere. The simple type is defined as:

    ```xml
    <xsd:simpleType name="ST_Index1">
        <xsd:restriction base="xsd:unsignedInt">
            <xsd:minInclusive value="1" />
        </xsd:restriction>
    </xsd:simpleType>
    ```

#### L.4.15.6.3.27 Adjust Handle

=== "中文"

    The complex type CT_Adj specifies a shape adjust handle modification. The shapes within a diagram can be modified based on their adjust handles, for example, the radius of the corner rounding in a rounded rectangle can be adjusted using this complex type. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Adj">
        <xsd:attribute name="idx" type="ST_Index1" use="required" />
        <xsd:attribute name="val" type="xsd:double" use="required" />
    </xsd:complexType>
    ```

=== "英文"

    **Adjust Handle**

    The complex type CT_Adj specifies a shape adjust handle modification. The shapes within a diagram can be modified based on their adjust handles, for example, the radius of the corner rounding in a rounded rectangle can be adjusted using this complex type. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Adj">
        <xsd:attribute name="idx" type="ST_Index1" use="required" />
        <xsd:attribute name="val" type="xsd:double" use="required" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.28 Adjust Handle List

=== "中文"

    The complex type CT_AdjLst holds all of the adjust handles for a given shape. The number of adjust handles accessible varies shape by shape, but there are usually less than four for a given shape. The complex type is defined in the following way:

    ```xml
    <xsd:complexType name="CT_AdjLst" o:cname="CAdjList">
        <xsd:sequence>
            <xsd:element name="adj" type="CT_Adj" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

=== "英文"

    **Adjust Handle List**

    The complex type CT_AdjLst holds all of the adjust handles for a given shape. The number of adjust handles accessible varies shape by shape, but there are usually less than four for a given shape. The complex type is defined in the following way:

    ```xml
    <xsd:complexType name="CT_AdjLst" o:cname="CAdjList">
        <xsd:sequence>
            <xsd:element name="adj" type="CT_Adj" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
    </xsd:complexType>
    ```

#### L.4.15.6.3.29 Shape

=== "中文"

    The complex type CT_Shape specifies a shape for a layout node. The shape complex type holds all of the information associated with the particular layout node and all of the adjustments or modifications that can be made to the shape. The rot attribute specifies a rotation on the shape. The blip attribute specifies an image that is used as a background fill for the shape and the blipPhldr attribute specifies whether or not the shape shows up with an image placeholder. The zOrderOff attribute specifies an offset to be used for the z-ordering of this shape, while the lkTxEntry attribute prevents text editing within the shape. A shape is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Shape">
        <xsd:sequence>
            <xsd:element name="adjLst" type="CT_AdjLst" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="rot" type="xsd:double" use="optional" default="0" />
        <xsd:attribute name="type" type="ST_LayoutShapeType" use="optional" default="none" />
        <xsd:attribute ref="r:blip" use="optional" />
        <xsd:attribute name="zOrderOff" type="xsd:int" use="optional" default="0" />
        <xsd:attribute name="hideGeom" type="xsd:boolean" use="optional" default="false" />
        <xsd:attribute name="lkTxEntry" type="xsd:boolean" use="optional" default="false" />
        <xsd:attribute name="blipPhldr" type="xsd:boolean" use="optional" default="false" />
    </xsd:complexType>
    ```

=== "英文"

    **Shape**

    The complex type CT_Shape specifies a shape for a layout node. The shape complex type holds all of the information associated with the particular layout node and all of the adjustments or modifications that can be made to the shape. The rot attribute specifies a rotation on the shape. The blip attribute specifies an image that is used as a background fill for the shape and the blipPhldr attribute specifies whether or not the shape shows up with an image placeholder. The zOrderOff attribute specifies an offset to be used for the z-ordering of this shape, while the lkTxEntry attribute prevents text editing within the shape. A shape is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Shape">
        <xsd:sequence>
            <xsd:element name="adjLst" type="CT_AdjLst" minOccurs="0" maxOccurs="1" />
        </xsd:sequence>
        <xsd:attribute name="rot" type="xsd:double" use="optional" default="0" />
        <xsd:attribute name="type" type="ST_LayoutShapeType" use="optional" default="none" />
        <xsd:attribute ref="r:blip" use="optional" />
        <xsd:attribute name="zOrderOff" type="xsd:int" use="optional" default="0" />
        <xsd:attribute name="hideGeom" type="xsd:boolean" use="optional" default="false" />
        <xsd:attribute name="lkTxEntry" type="xsd:boolean" use="optional" default="false" />
        <xsd:attribute name="blipPhldr" type="xsd:boolean" use="optional" default="false" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.30 Parameter

=== "中文"

    The complex type CT_Parameter holds the information regarding an algorithm parameter. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Parameter">
        <xsd:attribute name="type" type="ST_ParameterId" use="required" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

=== "英文"

    **Parameter**

    The complex type CT_Parameter holds the information regarding an algorithm parameter. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Parameter">
        <xsd:attribute name="type" type="ST_ParameterId" use="required" />
        <xsd:attribute name="val" type="xsd:string" use="required" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.31 Algorithm

=== "中文"

    The complex type CT_Algorithm defines the algorithm which the diagram uses to layout the nodes which contain the data. Also defined here are the optional list of parameters which are associated with this algorithm and modify its behavior. An algorithm is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Algorithm">
        <xsd:sequence>
            <xsd:element name="param" type="CT_Parameter" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="type" type="ST_AlgorithmType" use="required" />
        <xsd:attribute name="rev" type="xsd:unsignedInt" use="optional" default="0" />
    </xsd:complexType>
    ```

=== "英文"

    **Algorithm**

    The complex type CT_Algorithm defines the algorithm which the diagram uses to layout the nodes which contain the data. Also defined here are the optional list of parameters which are associated with this algorithm and modify its behavior. An algorithm is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Algorithm">
        <xsd:sequence>
            <xsd:element name="param" type="CT_Parameter" minOccurs="0" maxOccurs="unbounded" />
        </xsd:sequence>
        <xsd:attribute name="type" type="ST_AlgorithmType" use="required" />
        <xsd:attribute name="rev" type="xsd:unsignedInt" use="optional" default="0" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.32 Layout Node

=== "中文"

    The complex type CT_LayoutNode is the main building block of a diagram. A layout node contains enough information to lay out itself and its children. The name attribute is simply a unique string given to the layout node. The styleLbl attribute references the style label that is used to style the layout node. This style label has already been defined in this document. A layout node is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_LayoutNode">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="varLst" type="CT_LayoutVariablePropertySet" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attribute name="styleLbl" type="xsd:string" use="optional" />
        <xsd:attribute name="chOrder" type="ST_ChildOrderType" use="optional" default="b" />
        <xsd:attribute name="moveWith" type="xsd:IDREF" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Layout Node**

    The complex type CT_LayoutNode is the main building block of a diagram. A layout node contains enough information to lay out itself and its children. The name attribute is simply a unique string given to the layout node. The styleLbl attribute references the style label that is used to style the layout node. This style label has already been defined in this document. A layout node is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_LayoutNode">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="varLst" type="CT_LayoutVariablePropertySet" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attribute name="styleLbl" type="xsd:string" use="optional" />
        <xsd:attribute name="chOrder" type="ST_ChildOrderType" use="optional" default="b" />
        <xsd:attribute name="moveWith" type="xsd:IDREF" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.33 For Each

=== "中文"

    The complex type CT_ForEach defines a for each iterator. The iteration behaves as if it were a for each loop. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_ForEach">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attribute name="ref" type="xsd:IDREF" use="optional" />
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
    </xsd:complexType>
    ```

=== "英文"

    **For Each**

    The complex type CT_ForEach defines a for each iterator. The iteration behaves as if it were a for each loop. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_ForEach">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attribute name="ref" type="xsd:IDREF" use="optional" />
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.34 When

=== "中文"

    The complex type CT_When defines an if conditional expression. The complex type is usually used in conjunction with the else counterpart which is defined next. The CT_When complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_When">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Rules" minOccurs="0" maxOccurs="1" o:cname="Rules" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
        <xsd:attribute name="func" type="ST_FunctionType" use="required" />
        <xsd:attribute name="arg" type="ST_FunctionArgument" use="optional" />
        <xsd:attribute name="op" type="ST_FunctionValue" use="required" />
    </xsd:complexType>
    ```

=== "英文"

    **When**

    The complex type CT_When defines an if conditional expression. The complex type is usually used in conjunction with the else counterpart which is defined next. The CT_When complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_When">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Rules" minOccurs="0" maxOccurs="1" o:cname="Rules" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
        <xsd:attributeGroup ref="AG_IteratorAttributes" />
        <xsd:attribute name="func" type="ST_FunctionType" use="required" />
        <xsd:attribute name="arg" type="ST_FunctionArgument" use="optional" />
        <xsd:attribute name="op" type="ST_FunctionValue" use="required" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.35 Otherwise

=== "中文"

    The complex type CT_Otherwise is the else counterpart to the already defined if conditional expression. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Otherwise" o:cname="DDOtherwise">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Otherwise**

    The complex type CT_Otherwise is the else counterpart to the already defined if conditional expression. The complex type is defined as:

    ```xml
    <xsd:complexType name="CT_Otherwise" o:cname="DDOtherwise">
        <xsd:choice minOccurs="0" maxOccurs="unbounded">
            <xsd:element name="alg" type="CT_Algorithm" minOccurs="0" maxOccurs="1" />
            <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1" />
            <xsd:element name="presOf" type="CT_PresentationOf" minOccurs="0" maxOccurs="1" />
            <xsd:element name="constrLst" type="CT_Constraints" minOccurs="0" maxOccurs="1" />
            <xsd:element name="ruleLst" type="CT_Rules" minOccurs="0" maxOccurs="1" />
            <xsd:element name="forEach" type="CT_ForEach" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
            <xsd:element name="choose" type="CT_Choose" />
        </xsd:choice>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.36 Choose Statement

=== "中文"

    The complex type CT_Choose packages together the if and else conditions into an actual if/else statement. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Choose" o:cname="DDChoose">
        <xsd:sequence>
            <xsd:element name="if" type="CT_When" maxOccurs="unbounded" />
            <xsd:element name="else" type="CT_Otherwise" minOccurs="0" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Choose Statement**

    The complex type CT_Choose packages together the if and else conditions into an actual if/else statement. The complex type is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_Choose" o:cname="DDChoose">
        <xsd:sequence>
            <xsd:element name="if" type="CT_When" maxOccurs="unbounded" />
            <xsd:element name="else" type="CT_Otherwise" minOccurs="0" />
        </xsd:sequence>
        <xsd:attribute name="name" type="xsd:ID" use="optional" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.37 Sample Data

=== "中文"

    The complex type CT_SampleData defines how the data model is to be populated in an initial manner. The complex type holds a temporary data model when there is no data model present in order to display a diagram on an initial insert. The complex type is defined by:

    ```xml
    <xsd:complexType name="CT_SampleData">
        <xsd:sequence>
            <xsd:element name="dataModel" type="CT_DataModel" minOccurs="0" />
        </xsd:sequence>
        <xsd:attribute name="useDef" type="xsd:boolean" use="optional" default="false" />
    </xsd:complexType>
    ```

=== "英文"

    **Sample Data**

    The complex type CT_SampleData defines how the data model is to be populated in an initial manner. The complex type holds a temporary data model when there is no data model present in order to display a diagram on an initial insert. The complex type is defined by:

    ```xml
    <xsd:complexType name="CT_SampleData">
        <xsd:sequence>
            <xsd:element name="dataModel" type="CT_DataModel" minOccurs="0" />
        </xsd:sequence>
        <xsd:attribute name="useDef" type="xsd:boolean" use="optional" default="false" />
    </xsd:complexType>
    ```

#### L.4.15.6.3.38 Common Structures

=== "中文"

    CT_Category, CT_Categories, CT_Name, CT_Description, and ST_Version are defined just as their counterparts in the subclauses above, and they perform the same tasks.

=== "英文"

    **Common Structures**

    CT_Category, CT_Categories, CT_Name, CT_Description, and ST_Version are defined just as their counterparts in the subclauses above, and they perform the same tasks.

#### L.4.15.6.3.39 Diagram Definition

=== "中文"

    The complex type CT_DiagramDefinition is the root element for a diagram definition. It is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_DiagramDefinition">
        <xsd:sequence>
            <xsd:element name="title" type="CT_Name" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_Description" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_Categories" minOccurs="0" />
            <xsd:element name="sampData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="styleData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="clrData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_Version" use="optional" default="12.0" />
        <xsd:attribute name="defStyle" type="xsd:anyURI" use="optional" />
    </xsd:complexType>
    ```

=== "英文"

    **Diagram Definition**

    The complex type CT_DiagramDefinition is the root element for a diagram definition. It is defined in the following manner:

    ```xml
    <xsd:complexType name="CT_DiagramDefinition">
        <xsd:sequence>
            <xsd:element name="title" type="CT_Name" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="desc" type="CT_Description" minOccurs="0" maxOccurs="unbounded" />
            <xsd:element name="catLst" type="CT_Categories" minOccurs="0" />
            <xsd:element name="sampData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="styleData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="clrData" type="CT_SampleData" minOccurs="0" />
            <xsd:element name="layoutNode" type="CT_LayoutNode" />
        </xsd:sequence>
        <xsd:attribute name="uniqueId" type="xsd:anyURI" use="optional" />
        <xsd:attribute name="minVer" type="ST_Version" use="optional" default="12.0" />
        <xsd:attribute name="defStyle" type="xsd:anyURI" use="optional" />
    </xsd:complexType>
    ```
