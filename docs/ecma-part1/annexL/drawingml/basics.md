# L.4.1 基础

**Basics**

## L.4.1.1 测量单位 EMU

=== "中文"

    在整个 ECMA-376 中，EMU 用作长度测量单位。 EMU定义如下:

    1 emu $=\frac{1}{914400}$ US 英尺(inch) $=\frac{1}{360000}$ 厘米(cm)

    EMU 的创建是为了能够均匀划分英制和公制单位，以避免计算过程中的舍入错误。 EMU 的使用还有助于使用不同测量单位的不同区域之间实现更加无缝的系统切换和互操作性。 EMU 定义了一个基于整数的高精度坐标系。

=== "英文"

    **EMU Unit of Measurement**

    Throughout ECMA-376, the EMU is used as a unit of measurement for length. An EMU is defined as follows:

    1 emu $=\frac{1}{914400}$ US inch $=\frac{1}{360000}$ cm

    The EMU was created in order to be able to evenly divide in both English and Metric units, in order to avoid rounding errors during the calculation. The usage of EMUs also facilitates a more seamless system switch and interoperability between different locales utilizing different units of measurement. EMUs define an integer based, high precision coordinate system.

## L.4.1.2 介绍

=== "中文"

    这个子条款对DrawingML中描述的内容进行了高层次的概述。这些模式中的元素的聚合体涵盖了被标记为 DrawingML - Basics 子条款的内容。也就是说，这里包含的元素被认为是DrawingML框架中常见的共享元素。

=== "英文"

    **Introduction**

    This subclause provides a high-level overview of the content described in DrawingML. The aggregation of the elements within these schemas encompass what has been labeled the DrawingML – Basics subclause. That is, the elements contained here are considered to be commonly shared elements among the DrawingML framework.

## L.4.1.3 概览

=== "中文"

    这个子条款由四个独立的部分组成：基本元素、颜色、兼容性和锁定画布。这些部分共同构成了在DrawingML框架中共享的通用元素。下面将对这些元素进行描述。

=== "英文"

    **Overview**

    This sub-clause is made up of four distinct pieces: Basic Elements, Colors, Compatibility, and Locked Canvas. Together these make up the common elements that are shared across the DrawingML framework. These elements are described below.

## L.4.1.4 基本元素

=== "中文"

    当绘图ML框架的常见元素被聚合时，可以看到最常用的元素是属性元素。这些元素存在于每个对象中，并允许设置视觉和非视觉对象特定的属性。视觉属性是在对象在屏幕上呈现时影响其外观的属性。另一方面，非视觉属性不会影响对象的外观。相反，这些属性用于存储通常隐藏的信息，例如标识号、对象的可读名称以及在操作相应对象时应遵守的特定行为。

=== "英文"

    **Basic Elements**
    
    When the common elements of the DrawingML framework are aggregated it can be seen that the most widely used elements are property elements. These reside within every object and allow for the setting of both visual and non-visual object-specific properties. The visual properties are those that affect the appearance of the object when it is rendered on the screen. The non-visual properties on the other hand, do not affect the object's appearance. Instead, these properties are used to store information normally hidden such as identification numbers, human readable names for the objects and specific behaviour that should be obeyed within the UI when manipulating the corresponding object.

## L.4.1.5 色彩

=== "中文"

    色彩概念在文档中的DrawingML对象呈现中起着至关重要的作用。几乎所有对象都被指定为具有相应的颜色或一组颜色。色彩概念在图形应用程序中是常见的。由于这一点，以及当今有许多不同类型的图形对象可用，我们引入了几种不同类型的色彩模型的概念。以下色彩模型可用于在基于DrawingML的文档中指定颜色。

    1. RGB – 红绿蓝色模型 (Red, Green, Blue Color Model)
    2. HSL – 色调、饱和度、亮度颜色模型 (Hue, Saturation, Luminance Color Model)
    3. Scheme – 基于方案(Scheme)的颜色模型
    4. Preset – 基于预设(Preset)的颜色模型
    5. System – 操作系统(Operating System)颜色模型
    
    这些不同的模型允许文档作者选择适合其特定应用程序的颜色模型。这些模型的每一个都在DrawingML Basics参考资料中有详细说明。

=== "英文"

    **Colors**

    The notion of color plays a vital role in the presentation of DrawingML objects within a document. Virtually all objects are specified to have a corresponding color or set of colors. The notion of color is a common one among graphically-inclined applications. Because of this and the fact that there are many different kinds of graphic objects available today, we introduce the notion of several different types of color models. The following color models can be used to specify color within a DrawingML based document.

    1. RGB – Red, Green, Blue Color Model
    2. HSL – Hue, Saturation, Luminance Color Model
    3. Scheme – Scheme Based Color Model
    4. Preset – Color Presets Color Model
    5. System – Operating System Color Model
    
    These different models allow document authors the choice as to which color model would be appropriate for their particular application. Each of these is detailed within the DrawingML Basics reference material.

## L.4.1.6 兼容性

=== "中文"

    兼容性涉及遗留图纸(legacy drawings)的概念。遗留图纸是由先前版本的生成应用程序支持的对象，但现在不再作为选项提供。为了正确存储这些图纸对象，我们引入了遗留图纸兼容性的概念。这允许指定用于识别这个遗留对象(legacy object)的信息，从而在当前版本的生成应用程序中实现完整的渲染支持。

=== "英文"

    **Compatibility**

    Compatibility deals with the notion of legacy drawings. Legacy drawings are objects that were supported by previous versions of a generating application, but are no longer provided as an option. In order to store these drawing objects correctly, we introduce the notion of legacy drawing compatibility. This allows for the specification of information used to identify this legacy object and thus allow for full rendering support within current versions of the generating application.

## L.4.1.7 锁定画布

=== "中文"

    Locked Canvas是一个次要的话题，类似于兼容性，它用于渲染绘图对象，否则由于缺乏信息而无法识别。然而，Locked Canvas与兼容性方向相反，处理的是在当前版本的生成应用程序中创建和保存的对象，在先前版本的生成应用程序中打开的情况。Locked Canvas元素充当更高级绘图对象的容器。Locked Canvas的概念源自这样一个事实，即打开文件的生成应用程序无法创建此对象，因此也无法执行编辑。因此，绘图对象被锁定，无法进行通常会发生的所有UI调整。

=== "英文"

    **Locked Canvas**

    Locked Canvas is a minor topic that is similar to compatibility in that it is used to render drawing objects that would otherwise not be recognized due to a lack of information. Locked Canvas, however, goes in the opposite direction from compatibility, and deals with objects that have been created and saved in the current version of a generating application and are being opened in a previous version of the generating application. The locked canvas element acts as a container for more advanced drawing objects. The notion of a locked canvas comes from the fact that the generating application opening the file cannot create this object and thus cannot perform edits either. Thus, the drawing object is locked from all UI adjustments that would normally take place.
