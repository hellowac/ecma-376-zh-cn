# shared-documentPropertiesCustom.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/officeDocument/2006/custom-properties"
  xmlns:vt="http://schemas.openxmlformats.org/officeDocument/2006/docPropsVTypes"
  xmlns:s="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
  targetNamespace="http://schemas.openxmlformats.org/officeDocument/2006/custom-properties"
  blockDefault="#all" elementFormDefault="qualified">
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/docPropsVTypes"
    schemaLocation="shared-documentPropertiesVariantTypes.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
    schemaLocation="shared-commonSimpleTypes.xsd"/>
  <xsd:element name="Properties" type="CT_Properties"/>
  <xsd:complexType name="CT_Properties">
    <xsd:sequence>
      <xsd:element name="property" minOccurs="0" maxOccurs="unbounded" type="CT_Property"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Property">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element ref="vt:vector"/>
      <xsd:element ref="vt:array"/>
      <xsd:element ref="vt:blob"/>
      <xsd:element ref="vt:oblob"/>
      <xsd:element ref="vt:empty"/>
      <xsd:element ref="vt:null"/>
      <xsd:element ref="vt:i1"/>
      <xsd:element ref="vt:i2"/>
      <xsd:element ref="vt:i4"/>
      <xsd:element ref="vt:i8"/>
      <xsd:element ref="vt:int"/>
      <xsd:element ref="vt:ui1"/>
      <xsd:element ref="vt:ui2"/>
      <xsd:element ref="vt:ui4"/>
      <xsd:element ref="vt:ui8"/>
      <xsd:element ref="vt:uint"/>
      <xsd:element ref="vt:r4"/>
      <xsd:element ref="vt:r8"/>
      <xsd:element ref="vt:decimal"/>
      <xsd:element ref="vt:lpstr"/>
      <xsd:element ref="vt:lpwstr"/>
      <xsd:element ref="vt:bstr"/>
      <xsd:element ref="vt:date"/>
      <xsd:element ref="vt:filetime"/>
      <xsd:element ref="vt:bool"/>
      <xsd:element ref="vt:cy"/>
      <xsd:element ref="vt:error"/>
      <xsd:element ref="vt:stream"/>
      <xsd:element ref="vt:ostream"/>
      <xsd:element ref="vt:storage"/>
      <xsd:element ref="vt:ostorage"/>
      <xsd:element ref="vt:vstream"/>
      <xsd:element ref="vt:clsid"/>
    </xsd:choice>
    <xsd:attribute name="fmtid" use="required" type="s:ST_Guid"/>
    <xsd:attribute name="pid" use="required" type="xsd:int"/>
    <xsd:attribute name="name" use="optional" type="xsd:string"/>
    <xsd:attribute name="linkTarget" use="optional" type="xsd:string"/>
  </xsd:complexType>
</xsd:schema>
```
