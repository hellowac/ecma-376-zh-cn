---
hide:
  - toc
---

# shared-relationshipReference.xsd

- **前缀**: `r`
- **命名空间**: **`http://purl.oclc.org/ooxml/officeDocument/relationships`**

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://purl.oclc.org/ooxml/officeDocument/relationships"
  xmlns:r="http://purl.oclc.org/ooxml/officeDocument/relationships" elementFormDefault="qualified"
  targetNamespace="http://purl.oclc.org/ooxml/officeDocument/relationships" blockDefault="#all">
  <xsd:simpleType name="ST_RelationshipId">
    <xsd:restriction base="xsd:string"/>
  </xsd:simpleType>
  <xsd:attribute name="id" type="ST_RelationshipId"/>
  <xsd:attribute name="embed" type="ST_RelationshipId"/>
  <xsd:attribute name="link" type="ST_RelationshipId"/>
  <xsd:attribute name="dm" type="ST_RelationshipId" default=""/>
  <xsd:attribute name="lo" type="ST_RelationshipId" default=""/>
  <xsd:attribute name="qs" type="ST_RelationshipId" default=""/>
  <xsd:attribute name="cs" type="ST_RelationshipId" default=""/>
  <xsd:attribute name="blip" type="ST_RelationshipId" default=""/>
  <xsd:attribute name="pict" type="ST_RelationshipId"/>
  <xsd:attribute name="href" type="ST_RelationshipId"/>
  <xsd:attribute name="topLeft" type="ST_RelationshipId"/>
  <xsd:attribute name="topRight" type="ST_RelationshipId"/>
  <xsd:attribute name="bottomLeft" type="ST_RelationshipId"/>
  <xsd:attribute name="bottomRight" type="ST_RelationshipId"/>
</xsd:schema>
```
