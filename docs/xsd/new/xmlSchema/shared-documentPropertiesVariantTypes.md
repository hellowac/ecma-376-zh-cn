---
hide:
  - toc
---

# shared-documentPropertiesVariantTypes.xsd

- **前缀**: `vt`
- **命名空间**: **`http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes`**
- **相关命名空间**:
    - `vt`: **`http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes`**
    - `s`: [**`http://purl.oclc.org/ooxml/officeDocument/sharedTypes`**](./shared-commonSimpleTypes.md)

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes"
  xmlns:s="http://purl.oclc.org/ooxml/officeDocument/sharedTypes"
  targetNamespace="http://purl.oclc.org/ooxml/officeDocument/docPropsVTypes" 
  blockDefault="#all"
  elementFormDefault="qualified">
  <xsd:import namespace="http://purl.oclc.org/ooxml/officeDocument/sharedTypes"
    schemaLocation="shared-commonSimpleTypes.xsd"/>
  <xsd:simpleType name="ST_VectorBaseType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="variant"/>
      <xsd:enumeration value="i1"/>
      <xsd:enumeration value="i2"/>
      <xsd:enumeration value="i4"/>
      <xsd:enumeration value="i8"/>
      <xsd:enumeration value="ui1"/>
      <xsd:enumeration value="ui2"/>
      <xsd:enumeration value="ui4"/>
      <xsd:enumeration value="ui8"/>
      <xsd:enumeration value="r4"/>
      <xsd:enumeration value="r8"/>
      <xsd:enumeration value="lpstr"/>
      <xsd:enumeration value="lpwstr"/>
      <xsd:enumeration value="bstr"/>
      <xsd:enumeration value="date"/>
      <xsd:enumeration value="filetime"/>
      <xsd:enumeration value="bool"/>
      <xsd:enumeration value="cy"/>
      <xsd:enumeration value="error"/>
      <xsd:enumeration value="clsid"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_ArrayBaseType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="variant"/>
      <xsd:enumeration value="i1"/>
      <xsd:enumeration value="i2"/>
      <xsd:enumeration value="i4"/>
      <xsd:enumeration value="int"/>
      <xsd:enumeration value="ui1"/>
      <xsd:enumeration value="ui2"/>
      <xsd:enumeration value="ui4"/>
      <xsd:enumeration value="uint"/>
      <xsd:enumeration value="r4"/>
      <xsd:enumeration value="r8"/>
      <xsd:enumeration value="decimal"/>
      <xsd:enumeration value="bstr"/>
      <xsd:enumeration value="date"/>
      <xsd:enumeration value="bool"/>
      <xsd:enumeration value="cy"/>
      <xsd:enumeration value="error"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_Cy">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="\s*[0-9]*\.[0-9]{4}\s*"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_Error">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="\s*0x[0-9A-Za-z]{8}\s*"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Empty"/>
  <xsd:complexType name="CT_Null"/>
  <xsd:complexType name="CT_Vector">
    <xsd:choice minOccurs="1" maxOccurs="unbounded">
      <xsd:element ref="variant"/>
      <xsd:element ref="i1"/>
      <xsd:element ref="i2"/>
      <xsd:element ref="i4"/>
      <xsd:element ref="i8"/>
      <xsd:element ref="ui1"/>
      <xsd:element ref="ui2"/>
      <xsd:element ref="ui4"/>
      <xsd:element ref="ui8"/>
      <xsd:element ref="r4"/>
      <xsd:element ref="r8"/>
      <xsd:element ref="lpstr"/>
      <xsd:element ref="lpwstr"/>
      <xsd:element ref="bstr"/>
      <xsd:element ref="date"/>
      <xsd:element ref="filetime"/>
      <xsd:element ref="bool"/>
      <xsd:element ref="cy"/>
      <xsd:element ref="error"/>
      <xsd:element ref="clsid"/>
    </xsd:choice>
    <xsd:attribute name="baseType" type="ST_VectorBaseType" use="required"/>
    <xsd:attribute name="size" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Array">
    <xsd:choice minOccurs="1" maxOccurs="unbounded">
      <xsd:element ref="variant"/>
      <xsd:element ref="i1"/>
      <xsd:element ref="i2"/>
      <xsd:element ref="i4"/>
      <xsd:element ref="int"/>
      <xsd:element ref="ui1"/>
      <xsd:element ref="ui2"/>
      <xsd:element ref="ui4"/>
      <xsd:element ref="uint"/>
      <xsd:element ref="r4"/>
      <xsd:element ref="r8"/>
      <xsd:element ref="decimal"/>
      <xsd:element ref="bstr"/>
      <xsd:element ref="date"/>
      <xsd:element ref="bool"/>
      <xsd:element ref="error"/>
      <xsd:element ref="cy"/>
    </xsd:choice>
    <xsd:attribute name="lBounds" type="xsd:int" use="required"/>
    <xsd:attribute name="uBounds" type="xsd:int" use="required"/>
    <xsd:attribute name="baseType" type="ST_ArrayBaseType" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Variant">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element ref="variant"/>
      <xsd:element ref="vector"/>
      <xsd:element ref="array"/>
      <xsd:element ref="blob"/>
      <xsd:element ref="oblob"/>
      <xsd:element ref="empty"/>
      <xsd:element ref="null"/>
      <xsd:element ref="i1"/>
      <xsd:element ref="i2"/>
      <xsd:element ref="i4"/>
      <xsd:element ref="i8"/>
      <xsd:element ref="int"/>
      <xsd:element ref="ui1"/>
      <xsd:element ref="ui2"/>
      <xsd:element ref="ui4"/>
      <xsd:element ref="ui8"/>
      <xsd:element ref="uint"/>
      <xsd:element ref="r4"/>
      <xsd:element ref="r8"/>
      <xsd:element ref="decimal"/>
      <xsd:element ref="lpstr"/>
      <xsd:element ref="lpwstr"/>
      <xsd:element ref="bstr"/>
      <xsd:element ref="date"/>
      <xsd:element ref="filetime"/>
      <xsd:element ref="bool"/>
      <xsd:element ref="cy"/>
      <xsd:element ref="error"/>
      <xsd:element ref="stream"/>
      <xsd:element ref="ostream"/>
      <xsd:element ref="storage"/>
      <xsd:element ref="ostorage"/>
      <xsd:element ref="vstream"/>
      <xsd:element ref="clsid"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:complexType name="CT_Vstream">
    <xsd:simpleContent>
      <xsd:extension base="xsd:base64Binary">
        <xsd:attribute name="version" type="s:ST_Guid"/>
      </xsd:extension>
    </xsd:simpleContent>
  </xsd:complexType>
  <xsd:element name="variant" type="CT_Variant"/>
  <xsd:element name="vector" type="CT_Vector"/>
  <xsd:element name="array" type="CT_Array"/>
  <xsd:element name="blob" type="xsd:base64Binary"/>
  <xsd:element name="oblob" type="xsd:base64Binary"/>
  <xsd:element name="empty" type="CT_Empty"/>
  <xsd:element name="null" type="CT_Null"/>
  <xsd:element name="i1" type="xsd:byte"/>
  <xsd:element name="i2" type="xsd:short"/>
  <xsd:element name="i4" type="xsd:int"/>
  <xsd:element name="i8" type="xsd:long"/>
  <xsd:element name="int" type="xsd:int"/>
  <xsd:element name="ui1" type="xsd:unsignedByte"/>
  <xsd:element name="ui2" type="xsd:unsignedShort"/>
  <xsd:element name="ui4" type="xsd:unsignedInt"/>
  <xsd:element name="ui8" type="xsd:unsignedLong"/>
  <xsd:element name="uint" type="xsd:unsignedInt"/>
  <xsd:element name="r4" type="xsd:float"/>
  <xsd:element name="r8" type="xsd:double"/>
  <xsd:element name="decimal" type="xsd:decimal"/>
  <xsd:element name="lpstr" type="xsd:string"/>
  <xsd:element name="lpwstr" type="xsd:string"/>
  <xsd:element name="bstr" type="xsd:string"/>
  <xsd:element name="date" type="xsd:dateTime"/>
  <xsd:element name="filetime" type="xsd:dateTime"/>
  <xsd:element name="bool" type="xsd:boolean"/>
  <xsd:element name="cy" type="ST_Cy"/>
  <xsd:element name="error" type="ST_Error"/>
  <xsd:element name="stream" type="xsd:base64Binary"/>
  <xsd:element name="ostream" type="xsd:base64Binary"/>
  <xsd:element name="storage" type="xsd:base64Binary"/>
  <xsd:element name="ostorage" type="xsd:base64Binary"/>
  <xsd:element name="vstream" type="CT_Vstream"/>
  <xsd:element name="clsid" type="s:ST_Guid"/>
</xsd:schema>
```
