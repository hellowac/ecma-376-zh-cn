---
hide:
  - toc
---

# dml-lockedCanvas.xsd

- **前缀**: ``
- **命名空间**: **`http://purl.oclc.org/ooxml/drawingml/lockedCanvas`**
- **相关命名空间**:
    - `a`: [**`http://purl.oclc.org/ooxml/drawingml/main`**](./dml-main.md)
    - `r`: [**`http://purl.oclc.org/ooxml/officeDocument/relationships`**](./shared-relationshipReference.md)

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://purl.oclc.org/ooxml/drawingml/lockedCanvas"
  xmlns:a="http://purl.oclc.org/ooxml/drawingml/main"
  xmlns:r="http://purl.oclc.org/ooxml/officeDocument/relationships" 
  elementFormDefault="qualified" 
  targetNamespace="http://purl.oclc.org/ooxml/drawingml/lockedCanvas">
  <xsd:import namespace="http://purl.oclc.org/ooxml/drawingml/main" schemaLocation="dml-main.xsd"/>
  <xsd:element name="lockedCanvas" type="a:CT_GvmlGroupShape"/>
</xsd:schema>
```
