# Annex D. (informative) 示例中的命名空间前缀映射

=== "中文"

    在整个 ECMA-376 中，提供了 XML 语法来说明所记录的概念。 这些示例利用 XML 命名空间前缀，并且通常为简洁起见，不显示实际的命名空间映射。 本附件列出了这些示例中使用的命名空间前缀映射。

    | **前缀**   | **命名空间**                                                    |
    | ---------- | --------------------------------------------------------------- |
    | `a`        | `http://purl.oclc.org/ooxml/drawingml/main`                     |
    | `b`        | `http://purl.oclc.org/ooxml/officeDocument/bibliography`        |
    | `cp`       | `http://purl.oclc.org/ooxml/drawingml/chartDrawing`             |
    | `cdr`      | `http://schemas.openxmlformats.org/drawingml/2006/chartDrawing` |
    | `dc`       | `http://purl.org/dc/elements/1.1/`                              |
    | `dcmitype` | `http://purl.org/dc/dcmitype/`                                  |
    | `dcterms`  | `http://purl.org/dc/terms/`                                     |
    | `ds`       | `http://purl.oclc.org/ooxml/officeDocument/customXml`           |
    | `m`        | `http://purl.oclc.org/ooxml/officeDocument/math`                |
    | `o`        | `urn:schemas-microsoft-com:office:office`                       |
    | `p`        | `http://purl.oclc.org/ooxml/presentationml/main`                |
    | `pic`      | `http://purl.oclc.org/ooxml/drawingml/picture`                  |
    | `pvml`     | `urn:schemas-microsoft-com:office:powerpoint`                   |
    | `r`        | `http://purl.oclc.org/ooxml/officeDocument/relationships`       |
    | `sl`       | `http://purl.oclc.org/ooxml/schemaLibrary/main`                 |
    | `v`        | `urn:schemas-microsoft-com:vml`                                 |
    | `ve`       | `http://schemas.openxmlformats.org/markup-compatibility/2006`   |
    | `vt`       | `http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes`      |
    | `w`        | `http://purl.oclc.org/ooxml/wordprocessingml/main`              |
    | `w10`      | `urn:schemas-microsoft-com:office:word`                         |
    | `wp`       | `http://purl.oclc.org/ooxml/drawingml/wordprocessingDrawing`    |
    | `x`        | `urn:schemas-microsoft-com:office:excel`                        |
    | `xdr`      | `http://purl.oclc.org/ooxml/drawingml/spreadsheetDrawing`       |
    | `xsd`      | `http://www.w3.org/2001/XMLSchema`                              |
    | `xsi`      | `http://www.w3.org/2001/XMLSchema-instance`                     |

    如果未指定命名空间前缀，则应假定该元素或属性包含在父子条款定义的命名空间内。 例如，[第 18 节]中的无前缀元素包含在`http://purl.oclc.org/ooxml/spreadsheetml/main`命名空间中。

=== "英文"

    **Namespace Prefix Mapping in Examples**

    **This Annex is informative.**

    Throughout ECMA-376, XML syntax is provided to illustrate the concepts being documented. These examples leverage XML namespace prefixes, and, typically, for brevity, do not show the actual namespace mappings. This Annex lists the namespace prefix mappings that are used within these examples.

    | **Prefix** | **Namesapce**                                                   |
    | ---------- | --------------------------------------------------------------- |
    | `a`        | `http://purl.oclc.org/ooxml/drawingml/main`                     |
    | `b`        | `http://purl.oclc.org/ooxml/officeDocument/bibliography`        |
    | `cp`       | `http://purl.oclc.org/ooxml/drawingml/chartDrawing`             |
    | `cdr`      | `http://schemas.openxmlformats.org/drawingml/2006/chartDrawing` |
    | `dc`       | `http://purl.org/dc/elements/1.1/`                              |
    | `dcmitype` | `http://purl.org/dc/dcmitype/`                                  |
    | `dcterms`  | `http://purl.org/dc/terms/`                                     |
    | `ds`       | `http://purl.oclc.org/ooxml/officeDocument/customXml`           |
    | `m`        | `http://purl.oclc.org/ooxml/officeDocument/math`                |
    | `o`        | `urn:schemas-microsoft-com:office:office`                       |
    | `p`        | `http://purl.oclc.org/ooxml/presentationml/main`                |
    | `pic`      | `http://purl.oclc.org/ooxml/drawingml/picture`                  |
    | `pvml`     | `urn:schemas-microsoft-com:office:powerpoint`                   |
    | `r`        | `http://purl.oclc.org/ooxml/officeDocument/relationships`       |
    | `sl`       | `http://purl.oclc.org/ooxml/schemaLibrary/main`                 |
    | `v`        | `urn:schemas-microsoft-com:vml`                                 |
    | `ve`       | `http://schemas.openxmlformats.org/markup-compatibility/2006`   |
    | `vt`       | `http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes`      |
    | `w`        | `http://purl.oclc.org/ooxml/wordprocessingml/main`              |
    | `w10`      | `urn:schemas-microsoft-com:office:word`                         |
    | `wp`       | `http://purl.oclc.org/ooxml/drawingml/wordprocessingDrawing`    |
    | `x`        | `urn:schemas-microsoft-com:office:excel`                        |
    | `xdr`      | `http://purl.oclc.org/ooxml/drawingml/spreadsheetDrawing`       |
    | `xsd`      | `http://www.w3.org/2001/XMLSchema`                              |
    | `xsi`      | `http://www.w3.org/2001/XMLSchema-instance`                     |

    If no namespace prefix is specified, it should be assumed that that element or attribute is contained  within the namespace defined by the parent subclause. For example, unprefixed elements in [§18] are  contained in the `http://purl.oclc.org/ooxml/spreadsheetml/main` namespace.

    End informative Annex.
