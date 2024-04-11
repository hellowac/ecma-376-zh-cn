# ECMA-376-1:2016 - Part 1

Office Open XML 文件格式 - 基础知识和标记语言参考

Office Open XML File Formats — Fundamentals and Markup Language Reference

## 前言

=== "中文"

    **前言**

    对第 4 版的修改是为了使第 5 版标准与 ISO/IEC 29500:2016 保持一致。第 5 版和 ISO/IEC 29500:2016 均引用第 1 版。因此，第五版不会取消或取代第一版。 然而，第五版确实取消并取代了第四版。

    [附录 M] 中给出了 ECMA-376:2016 和 ECMA-376:2006 之间的一些重要差异.

    ECMA-376 由以下部分组成：

    * Part 1: 基础知识和标记语言参考(Fundamentals and Markup Language Reference)
    * Part 2: 开放打包约定(Open Packaging Conventions)
    * Part 3: 标记兼容性和可扩展性(Markup Compatibility and Extensibility)
    * Part 4: 过渡性迁移功能(Transitional Migration Features)
    

    附录 A、F 和 G 构成 ECMA-376 本部分的规范部分。 附录 B-E 和 H-M 仅供参考。
    
    ECMA-376 的本部分包括五个附录（附录 A、附录 B、附录 F、附录 G 和附录 H），涉及以电子形式提供的数据文件。

    本部分定义的文档表示格式与 ECMA-376:2006 相应部分中定义的格式不同。 一些差异反映在模式(schema)更新中，如本部分的[附录 M]所示。

=== "英文"

    **Foreword**

    Changes from the 4th edition were made to align this 5th edition Standard with ISO/IEC 29500:2016. Both this 5th edition and ISO/IEC 29500:2016 refer to the 1st edition. As such, this 5th edition does not cancel or replace the 1st edition. This 5th edition does, however, cancel and replace the 4th edition.”

    Some important differences between ECMA-376:2016 and ECMA-376:2006 are given in [Annex M].

    ECMA-376 consists of the following parts:

    * Part 1: Fundamentals and Markup Language Reference
    * Part 2: Open Packaging Conventions
    * Part 3: Markup Compatibility and Extensibility
    * Part 4: Transitional Migration Features
    
    Annexes A, F and G form a normative part of this Part of ECMA-376. Annexes B–E and H–M are for information only.
    
    This Part of ECMA-376 includes five annexes (Annex A, Annex B, Annex F, Annex G, and Annex H) that refer to data files provided in electronic form.

    The document representation formats defined by this Part are different from the formats defined in the corresponding Part of ECMA-376:2006. Some of the differences are reflected in schema changes, as shown in Annex M of this Part.

## 简介

=== "中文"

    ECMA-376 指定了一系列 XML Schema，统称为 Office Open XML，它定义了文字处理、电子表格和演示文稿文档的 XML 词汇表，以及符合这些模式的文档的打包方式。

    目标是通过最广泛的工具和平台实现 Office Open XML 格式，促进办公生产力应用程序和业务线系统之间的互操作性，并支持和加强文档归档和保存，所有这些都在一种与现有 Microsoft Office 文档库完全兼容的方式实现。

=== "英文"

    **Introduction**

    ECMA-376 specifies a family of XML schemas, collectively called Office Open XML, which define the XML vocabularies for word-processing, spreadsheet, and presentation documents, as well as the packaging of documents that conform to these schemas.

    The goal is to enable the implementation of the Office Open XML formats by the widest set of tools and platforms, fostering interoperability across office productivity applications and line-of-business systems, as well as to support and strengthen document archival and preservation, all in a way that is fully compatible with the existing corpus of Microsoft Office documents.

<!--锚点zh-cn-->

[第 2.1 节]: #21-文档一致性
[第 2.3 节]: #23-应用程序描述
[第 4 节]: #4-术语和定义
[第 11.3 节]: #113-部件概览
[第 12.3 节]: #123-部件概览
[第 13.3 节]: #133-部件概览
[第 14.2 节]: #142-部件概览
[第 15.2 节]: #152-部件概览
[第 16 节]: #16-部件概览
[第 18 节]: #18-spareadsheetml-参考资料
[附录 A]: #annex-a-normative-schemas---w3c-xml-schema

<!--锚点en-->

[§2.1]: #21-drawingml---组件参考资料
[§2.3]: #23-应用程序描述
[§4]: #4-术语和定义
[§11.3]: #113-部件概览
[§11.3.1]: #1131-替代格式导入部件
[§11.3.2]: #1132-评论部件
[§11.3.3]: #1133-文档设置部件
[§11.3.4]: #1134-尾注部件
[§11.3.5]: #1135-字体表部件
[§11.3.6]: #1136-页脚部件
[§11.3.7]: #1137-脚注部件
[§11.3.8]: #1138-术语表部件
[§11.3.9]: #1139-头部部件
[§11.3.10]: #11310-主文档部件
[§11.3.11]: #11311-编号定义部件
[§11.3.12]: #11312-样式定义部件
[§11.3.13]: #11313-web设置部件
[§12.3]: #123-部件概览
[§13.1]: #131-presentationml-特定术语词汇表
[§13.2]: #132-包结构
[§13.3]: #133-部件概览
[§13.3.1]: #1331-评论作者部件
[§13.3.2]: #1332-评论部件
[§13.3.3]: #1333-讲义母板部件
[§13.3.4]: #1334-笔记母版部件
[§13.3.5]: #1335-笔记幻灯片部件
[§13.3.6]: #1336-演示部件
[§13.3.7]: #1337-演示属性部件
[§13.3.8]: #1338-幻灯片部件
[§13.3.9]: #1339-幻灯片布局部件
[§13.3.10]: #13310-幻灯片母版部件
[§13.3.11]: #13311-幻灯片同步数据部件
[§13.3.12]: #13312-用户已定义标签部件
[§13.3.13]: #13313-视图属性部件
[§14]: #14-drawingml
[§14.2]: #142-部件概览
[§14.2.1]: #1421-图表部件
[§14.2.2]: #1422-图表绘制部件
[§14.2.3]: #1423-绘制颜色部件
[§14.2.4]: #1424-绘制数据部件
[§14.2.5]: #1425-绘制布局定义部件
[§14.2.6]: #1426-绘制样式部件
[§14.2.7]: #1427-主题部件
[§14.2.8]: #1428-主题覆盖部件
[§14.2.9]: #1429-表格样式部件
[§15]: #15-共享
[§15.1]: #151-共享术语词汇表
[§15.2]: #152-部件概览
[§15.2.1]: #1521-附加特性部件
[§15.2.2]: #1522-音频部件
[§15.2.3]: #1523-参考书目部件
[§15.2.4]: #1524-内容部件
[§15.2.5]: #1525-自定义xml数据存储部件
[§15.2.6]: #1526-自定义-xml-数据存储属性部件
[§15.2.7]: #1527-数字签名起源部件
[§15.2.8]: #1528-数字签名-xml-签名部件
[§15.2.9]: #1529-嵌入式控制持久化部件
[§15.2.10]: #15210-嵌入对象部件
[§15.2.11]: #15211-嵌入包部件
[§15.2.12]: #15212-文件属性部件
[§15.2.12.1]: #152121-核心文件属性部件
[§15.2.12.2]: #152122-自定义文件属性部件
[§15.2.12.3]: #152123-扩展文件属性部件
[§15.2.13]: #15213-字体部件
[§15.2.14]: #15214-图片部件
[§15.2.15]: #15215-打印机设置部件
[§15.2.16]: #1526-自定义-xml-数据存储属性部件
[§15.2.17]: #15217-视频部件
[§15.3]: #153-超链接
[§16]: #16-部件概览
[§18]: #18-spareadsheetml-参考资料
[Annex A]: #annex-a-normative-schemas---w3c-xml-schema
