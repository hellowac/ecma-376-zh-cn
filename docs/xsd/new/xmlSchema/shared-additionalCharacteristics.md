---
hide:
  - toc
---

# shared-additionalCharacteristics.xsd

- **前缀**: ``
- **命名空间**: **`http://purl.oclc.org/ooxml/officeDocument/characteristics`**

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://purl.oclc.org/ooxml/officeDocument/characteristics"
  targetNamespace="http://purl.oclc.org/ooxml/officeDocument/characteristics"
  elementFormDefault="qualified">
  <xsd:complexType name="CT_AdditionalCharacteristics">
    <xsd:sequence>
      <xsd:element name="characteristic" type="CT_Characteristic" minOccurs="0"
        maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Characteristic">
    <xsd:attribute name="name" type="xsd:string" use="required"/>
    <xsd:attribute name="relation" type="ST_Relation" use="required"/>
    <xsd:attribute name="val" type="xsd:string" use="required"/>
    <xsd:attribute name="vocabulary" type="xsd:anyURI" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Relation">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="ge"/>
      <xsd:enumeration value="le"/>
      <xsd:enumeration value="gt"/>
      <xsd:enumeration value="lt"/>
      <xsd:enumeration value="eq"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:element name="additionalCharacteristics" type="CT_AdditionalCharacteristics"/>
</xsd:schema>
```
