# shared-documentPropertiesExtended.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/officeDocument/2006/extended-properties"
  xmlns:vt="http://schemas.openxmlformats.org/officeDocument/2006/docPropsVTypes"
  targetNamespace="http://schemas.openxmlformats.org/officeDocument/2006/extended-properties"
  elementFormDefault="qualified" blockDefault="#all">
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/docPropsVTypes"
    schemaLocation="shared-documentPropertiesVariantTypes.xsd"/>
  <xsd:element name="Properties" type="CT_Properties"/>
  <xsd:complexType name="CT_Properties">
    <xsd:all>
      <xsd:element name="Template" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="Manager" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="Company" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="Pages" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="Words" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="Characters" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="PresentationFormat" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="Lines" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="Paragraphs" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="Slides" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="Notes" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="TotalTime" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="HiddenSlides" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="MMClips" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="ScaleCrop" minOccurs="0" maxOccurs="1" type="xsd:boolean"/>
      <xsd:element name="HeadingPairs" minOccurs="0" maxOccurs="1" type="CT_VectorVariant"/>
      <xsd:element name="TitlesOfParts" minOccurs="0" maxOccurs="1" type="CT_VectorLpstr"/>
      <xsd:element name="LinksUpToDate" minOccurs="0" maxOccurs="1" type="xsd:boolean"/>
      <xsd:element name="CharactersWithSpaces" minOccurs="0" maxOccurs="1" type="xsd:int"/>
      <xsd:element name="SharedDoc" minOccurs="0" maxOccurs="1" type="xsd:boolean"/>
      <xsd:element name="HyperlinkBase" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="HLinks" minOccurs="0" maxOccurs="1" type="CT_VectorVariant"/>
      <xsd:element name="HyperlinksChanged" minOccurs="0" maxOccurs="1" type="xsd:boolean"/>
      <xsd:element name="DigSig" minOccurs="0" maxOccurs="1" type="CT_DigSigBlob"/>
      <xsd:element name="Application" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="AppVersion" minOccurs="0" maxOccurs="1" type="xsd:string"/>
      <xsd:element name="DocSecurity" minOccurs="0" maxOccurs="1" type="xsd:int"/>
    </xsd:all>
  </xsd:complexType>
  <xsd:complexType name="CT_VectorVariant">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element ref="vt:vector"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_VectorLpstr">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element ref="vt:vector"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DigSigBlob">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element ref="vt:blob"/>
    </xsd:sequence>
  </xsd:complexType>
</xsd:schema>
```
