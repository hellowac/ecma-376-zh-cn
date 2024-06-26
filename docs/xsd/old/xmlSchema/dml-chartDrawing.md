# dml-chartDrawing.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="<http://www.w3.org/2001/XMLSchema>"
  xmlns:a="<http://schemas.openxmlformats.org/drawingml/2006/main>"
  xmlns="<http://schemas.openxmlformats.org/drawingml/2006/chartDrawing>"
  targetNamespace="<http://schemas.openxmlformats.org/drawingml/2006/chartDrawing>"
  elementFormDefault="qualified">
  <xsd:import namespace="<http://schemas.openxmlformats.org/drawingml/2006/main>"
    schemaLocation="dml-main.xsd"/>
  <xsd:complexType name="CT_ShapeNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvSpPr" type="a:CT_NonVisualDrawingShapeProps" minOccurs="1" maxOccurs="1"
      />
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Shape">
    <xsd:sequence>
      <xsd:element name="nvSpPr" type="CT_ShapeNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txBody" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="macro" type="xsd:string" use="optional"/>
    <xsd:attribute name="textlink" type="xsd:string" use="optional"/>
    <xsd:attribute name="fLocksText" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="fPublished" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ConnectorNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvCxnSpPr" type="a:CT_NonVisualConnectorProperties" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Connector">
    <xsd:sequence>
      <xsd:element name="nvCxnSpPr" type="CT_ConnectorNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="macro" type="xsd:string" use="optional"/>
    <xsd:attribute name="fPublished" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PictureNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvPicPr" type="a:CT_NonVisualPictureProperties" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Picture">
    <xsd:sequence>
      <xsd:element name="nvPicPr" type="CT_PictureNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blipFill" type="a:CT_BlipFillProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="macro" type="xsd:string" use="optional" default=""/>
    <xsd:attribute name="fPublished" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicFrameNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"
        minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicFrame">
    <xsd:sequence>
      <xsd:element name="nvGraphicFramePr" type="CT_GraphicFrameNonVisual" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="xfrm" type="a:CT_Transform2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element ref="a:graphic" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="macro" type="xsd:string" use="optional"/>
    <xsd:attribute name="fPublished" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_GroupShapeNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGrpSpPr" type="a:CT_NonVisualGroupDrawingShapeProps" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_GroupShape">
    <xsd:sequence>
      <xsd:element name="nvGrpSpPr" type="CT_GroupShapeNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="grpSpPr" type="a:CT_GroupShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:choice minOccurs="0" maxOccurs="unbounded">
        <xsd:element name="sp" type="CT_Shape"/>
        <xsd:element name="grpSp" type="CT_GroupShape"/>
        <xsd:element name="graphicFrame" type="CT_GraphicFrame"/>
        <xsd:element name="cxnSp" type="CT_Connector"/>
        <xsd:element name="pic" type="CT_Picture"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_ObjectChoices">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="sp" type="CT_Shape"/>
        <xsd:element name="grpSp" type="CT_GroupShape"/>
        <xsd:element name="graphicFrame" type="CT_GraphicFrame"/>
        <xsd:element name="cxnSp" type="CT_Connector"/>
        <xsd:element name="pic" type="CT_Picture"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:group>
  <xsd:simpleType name="ST_MarkerCoordinate">
    <xsd:restriction base="xsd:double">
      <xsd:minInclusive value="0.0"/>
      <xsd:maxInclusive value="1.0"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Marker">
    <xsd:sequence>
      <xsd:element name="x" type="ST_MarkerCoordinate" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="y" type="ST_MarkerCoordinate" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_RelSizeAnchor">
    <xsd:sequence>
      <xsd:element name="from" type="CT_Marker"/>
      <xsd:element name="to" type="CT_Marker"/>
      <xsd:group ref="EG_ObjectChoices"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_AbsSizeAnchor">
    <xsd:sequence>
      <xsd:element name="from" type="CT_Marker"/>
      <xsd:element name="ext" type="a:CT_PositiveSize2D"/>
      <xsd:group ref="EG_ObjectChoices"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_Anchor">
    <xsd:choice>
      <xsd:element name="relSizeAnchor" type="CT_RelSizeAnchor"/>
      <xsd:element name="absSizeAnchor" type="CT_AbsSizeAnchor"/>
    </xsd:choice>
  </xsd:group>
  <xsd:complexType name="CT_Drawing">
    <xsd:sequence>
      <xsd:group ref="EG_Anchor" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
</xsd:schema>
```
