# dml-picture.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/drawingml/2006/picture"
  xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main" elementFormDefault="qualified"
  targetNamespace="http://schemas.openxmlformats.org/drawingml/2006/picture">
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/main"
    schemaLocation="dml-main.xsd"/>
  <xsd:complexType name="CT_PictureNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvPicPr" type="a:CT_NonVisualPictureProperties" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Picture">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="nvPicPr" type="CT_PictureNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blipFill" type="a:CT_BlipFillProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="pic" type="CT_Picture"/>
</xsd:schema>
```
