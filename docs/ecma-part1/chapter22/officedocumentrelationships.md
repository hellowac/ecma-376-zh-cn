# 22.8 Office 文档关系

=== "中文"

    在 Office Open XML 文档中，必须能够从包中的一个部件显式引用另一个部件。[例如: PresentationML Slide 需要能够显式引用其中的每张图片，以了解每张图片的锚定位置。]

    为了确保在文档中可以轻松识别所有此类显式关系引用，所有此类关系都包含在此名称空间中的属性内。 因此，此命名空间仅用于定义整个 Office Open XML 中使用的属性以创建显式关系，以及此类属性的单个简单类型。

=== "英文"

    **Office Document Relationships**

    Within an Office Open XML document, it is necessary to be able to explicitly reference one part within the package from another [Example: A PresentationML Slide needs to be able to explicitly reference each picture within it to know where each one is anchored. end example]
    
    In order to ensure that all such explicit relationship references are easily identifiable within a document, all such relationships are included within attributes in this namespace. This namespace therefore only serves to define attributes used throughout Office Open XML to create explicit relationships, and a single simple type for such attributes.

## 22.8.1 目录

=== "中文"

    - 22.8.2 Simple Types
        - 22.8.2.1 ST_RelationshipId (Explicit Relationship ID)

=== "英文"

    **Table of Contents**

    **This subclause is informative.**

    - 22.8.2 Simple Types
        - 22.8.2.1 ST_RelationshipId (Explicit Relationship ID)

## 22.8.2 简单类型

=== "中文"

    这是专用于 Office 文档关系的简单类型的完整列表。

=== "英文"

    **Simple Types**

    This is the complete list of simple types dedicated to Office Document Relationships.

### 22.8.2.1 ST_RelationshipId (显式关系 ID)

=== "中文"

    此简单类型指定部件关系项中的关系 ID，该关系项是来自父 XML 元素的显式关系的目标。

    作为指定关系目标的关系类型应根据父 XML 元素的上下文来确定。

    !!! info "Example"
    
        考虑 Office Open XML 文档中的以下标记：

        ```xml
        <… r:id="rId5" />
        ```

    `id` 属性的类型为 `ST_RelationshipID`，因此基于父 XML 元素的上下文，具有 ID rId5 的关系必须是源部分的显式关系的目标。
    
    此简单类型的内容是 W3C XML Schema字符串(string)数据类型的限制。

    [注意: 此简单类型的内容模型 (`ST_RelationshipId`) 的 W3C XML 架构定义位于 [§A.6.8] 中。]

=== "英文"

    **ST_RelationshipId (Explicit Relationship ID)**
    
    This simple type specifies the relationship ID in a part's relationship item which is the target of an explicit relationship from the parent XML element.

    The kind of relationship which shall be the target of the relationship specified shall be determined based on the context of the parent XML element.

    !!! info "Example"
    
        Consider the following markup in an Office Open XML document:

        ```xml
        <… r:id="rId5" />
        ```

    The id attribute is of type ST_RelationshipID, and therefore the relationship with ID rId5 must be the target of an explicit relationship from the source part, based on the context of the parent XML element.

    This simple type's contents are a restriction of the W3C XML Schema string datatype.

    [Note: The W3C XML Schema definition of this simple type’s content model (ST_RelationshipId) is located in [§A.6.8]. end note]
