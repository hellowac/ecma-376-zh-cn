# 20.3 DrawingML - Locked Canvas

=== "中文"

    在 DrawingML 对象内，锁定的画布允许以托管应用程序可以查看但不能编辑的格式放置 DrawingML 对象。 这使得应用程序不支持的 DrawingML 对象可以包含在无法编辑的应用程序中并在其中查看。

=== "英文"

    **DrawingML - Locked Canvas**

    Within a DrawingML object, a locked canvas allows DrawingML objects to be placed in a format where they can be viewed but not edited by the hosting application. This allows DrawingML objects not supported by an application to be included and viewed in applications where they cannot be edited.

## 20.3.1 Table of Contents

=== "中文"

    - [20.3.2 基础](#2032-基础)
        - [20.3.2.1 lockedCanvas (锁定画布容器)](#20321-lockedcanvas-锁定画布容器)

=== "英文"

    **This subclause is informative.**

    20.3.2 Basics
    20.3.2.1 lockedCanvas (Locked Canvas Container)
    
    **End of informative text.**

## 20.3.2 基础

=== "中文"

    本节指定基本 DrawingML 框架内的锁定画布

=== "英文"

    **Basics**

    This section specifies a locked canvas within the basic DrawingML framework

### 20.3.2.1 lockedCanvas (锁定画布容器)

=== "中文"

    锁定的画布元素充当更高级绘图对象的容器。 锁定画布的概念来自这样一个事实：打开文件的生成应用程序无法创建该对象，因此也无法执行编辑。 因此，绘图对象被锁定，无法进行通常发生的所有 UI 调整。

    [Note: 该元素内容模型 (CT_GvmlGroupShape) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **lockedCanvas (Locked Canvas Container)**

    The locked canvas element acts as a container for more advanced drawing objects. The notion of a locked canvas comes from the fact that the generating application opening the file cannot create this object and can thus not perform edits either. Thus the drawing object is locked from all UI adjustments that would normally take place.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlGroupShape) is located in §A.4.1. end note]
