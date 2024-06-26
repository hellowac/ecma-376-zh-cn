# dml-spreadsheetDrawing.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main"
  xmlns="http://schemas.openxmlformats.org/drawingml/2006/spreadsheetDrawing"
  xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
  targetNamespace="http://schemas.openxmlformats.org/drawingml/2006/spreadsheetDrawing"
  elementFormDefault="qualified">
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/main"
    schemaLocation="dml-main.xsd"/>
  <xsd:import schemaLocation="shared-relationshipReference.xsd"
    namespace="http://schemas.openxmlformats.org/officeDocument/2006/relationships"/>
  <xsd:element name="from" type="CT_Marker"/>
  <xsd:element name="to" type="CT_Marker"/>
  <xsd:complexType name="CT_AnchorClientData">
    <xsd:attribute name="fLocksWithSheet" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="fPrintsWithSheet" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
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
  <xsd:complexType name="CT_GraphicalObjectFrameNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"
        minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicalObjectFrame">
    <xsd:sequence>
      <xsd:element name="nvGraphicFramePr" type="CT_GraphicalObjectFrameNonVisual" minOccurs="1"
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
        <xsd:element name="graphicFrame" type="CT_GraphicalObjectFrame"/>
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
        <xsd:element name="graphicFrame" type="CT_GraphicalObjectFrame"/>
        <xsd:element name="cxnSp" type="CT_Connector"/>
        <xsd:element name="pic" type="CT_Picture"/>
        <xsd:element name="contentPart" type="CT_Rel"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_Rel">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_ColID">
    <xsd:restriction base="xsd:int">
      <xsd:minInclusive value="0"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_RowID">
    <xsd:restriction base="xsd:int">
      <xsd:minInclusive value="0"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Marker">
    <xsd:sequence>
      <xsd:element name="col" type="ST_ColID"/>
      <xsd:element name="colOff" type="a:ST_Coordinate"/>
      <xsd:element name="row" type="ST_RowID"/>
      <xsd:element name="rowOff" type="a:ST_Coordinate"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_EditAs">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="twoCell"/>
      <xsd:enumeration value="oneCell"/>
      <xsd:enumeration value="absolute"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TwoCellAnchor">
    <xsd:sequence>
      <xsd:element name="from" type="CT_Marker"/>
      <xsd:element name="to" type="CT_Marker"/>
      <xsd:group ref="EG_ObjectChoices"/>
      <xsd:element name="clientData" type="CT_AnchorClientData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="editAs" type="ST_EditAs" use="optional" default="twoCell"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OneCellAnchor">
    <xsd:sequence>
      <xsd:element name="from" type="CT_Marker"/>
      <xsd:element name="ext" type="a:CT_PositiveSize2D"/>
      <xsd:group ref="EG_ObjectChoices"/>
      <xsd:element name="clientData" type="CT_AnchorClientData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_AbsoluteAnchor">
    <xsd:sequence>
      <xsd:element name="pos" type="a:CT_Point2D"/>
      <xsd:element name="ext" type="a:CT_PositiveSize2D"/>
      <xsd:group ref="EG_ObjectChoices"/>
      <xsd:element name="clientData" type="CT_AnchorClientData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_Anchor">
    <xsd:choice>
      <xsd:element name="twoCellAnchor" type="CT_TwoCellAnchor"/>
      <xsd:element name="oneCellAnchor" type="CT_OneCellAnchor"/>
      <xsd:element name="absoluteAnchor" type="CT_AbsoluteAnchor"/>
    </xsd:choice>
  </xsd:group>
  <xsd:complexType name="CT_Drawing">
    <xsd:sequence>
      <xsd:group ref="EG_Anchor" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="wsDr" type="CT_Drawing"/>
</xsd:schema>
```