# dml-wordprocessingDrawing.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main"
  xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"
  xmlns:dpct="http://schemas.openxmlformats.org/drawingml/2006/picture"
  xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
  xmlns="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"
  targetNamespace="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"
  elementFormDefault="qualified">
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/main"
    schemaLocation="dml-main.xsd"/>
  <xsd:import schemaLocation="wml.xsd"
    namespace="http://schemas.openxmlformats.org/wordprocessingml/2006/main"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/picture"
    schemaLocation="dml-picture.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    schemaLocation="shared-relationshipReference.xsd"/>
  <xsd:complexType name="CT_EffectExtent">
    <xsd:attribute name="l" type="a:ST_Coordinate" use="required"/>
    <xsd:attribute name="t" type="a:ST_Coordinate" use="required"/>
    <xsd:attribute name="r" type="a:ST_Coordinate" use="required"/>
    <xsd:attribute name="b" type="a:ST_Coordinate" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_WrapDistance">
    <xsd:restriction base="xsd:unsignedInt"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_Inline">
    <xsd:sequence>
      <xsd:element name="extent" type="a:CT_PositiveSize2D"/>
      <xsd:element name="effectExtent" type="CT_EffectExtent" minOccurs="0"/>
      <xsd:element name="docPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"
        minOccurs="0" maxOccurs="1"/>
      <xsd:element ref="a:graphic" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="distT" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distB" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distL" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distR" type="ST_WrapDistance" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_WrapText">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="bothSides"/>
      <xsd:enumeration value="left"/>
      <xsd:enumeration value="right"/>
      <xsd:enumeration value="largest"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_WrapPath">
    <xsd:sequence>
      <xsd:element name="start" type="a:CT_Point2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="lineTo" type="a:CT_Point2D" minOccurs="2" maxOccurs="unbounded"/>
    </xsd:sequence>
    <xsd:attribute name="edited" type="xsd:boolean" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WrapNone"/>
  <xsd:complexType name="CT_WrapSquare">
    <xsd:sequence>
      <xsd:element name="effectExtent" type="CT_EffectExtent" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="wrapText" type="ST_WrapText" use="required"/>
    <xsd:attribute name="distT" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distB" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distL" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distR" type="ST_WrapDistance" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WrapTight">
    <xsd:sequence>
      <xsd:element name="wrapPolygon" type="CT_WrapPath" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="wrapText" type="ST_WrapText" use="required"/>
    <xsd:attribute name="distL" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distR" type="ST_WrapDistance" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WrapThrough">
    <xsd:sequence>
      <xsd:element name="wrapPolygon" type="CT_WrapPath" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="wrapText" type="ST_WrapText" use="required"/>
    <xsd:attribute name="distL" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distR" type="ST_WrapDistance" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WrapTopBottom">
    <xsd:sequence>
      <xsd:element name="effectExtent" type="CT_EffectExtent" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="distT" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distB" type="ST_WrapDistance" use="optional"/>
  </xsd:complexType>
  <xsd:group name="EG_WrapType">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="wrapNone" type="CT_WrapNone" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="wrapSquare" type="CT_WrapSquare" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="wrapTight" type="CT_WrapTight" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="wrapThrough" type="CT_WrapThrough" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="wrapTopAndBottom" type="CT_WrapTopBottom" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:group>
  <xsd:simpleType name="ST_PositionOffset">
    <xsd:restriction base="xsd:int"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_AlignH">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="left"/>
      <xsd:enumeration value="right"/>
      <xsd:enumeration value="center"/>
      <xsd:enumeration value="inside"/>
      <xsd:enumeration value="outside"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_RelFromH">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="margin"/>
      <xsd:enumeration value="page"/>
      <xsd:enumeration value="column"/>
      <xsd:enumeration value="character"/>
      <xsd:enumeration value="leftMargin"/>
      <xsd:enumeration value="rightMargin"/>
      <xsd:enumeration value="insideMargin"/>
      <xsd:enumeration value="outsideMargin"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PosH">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="align" type="ST_AlignH" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="posOffset" type="ST_PositionOffset" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="relativeFrom" type="ST_RelFromH" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_AlignV">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="top"/>
      <xsd:enumeration value="bottom"/>
      <xsd:enumeration value="center"/>
      <xsd:enumeration value="inside"/>
      <xsd:enumeration value="outside"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_RelFromV">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="margin"/>
      <xsd:enumeration value="page"/>
      <xsd:enumeration value="paragraph"/>
      <xsd:enumeration value="line"/>
      <xsd:enumeration value="topMargin"/>
      <xsd:enumeration value="bottomMargin"/>
      <xsd:enumeration value="insideMargin"/>
      <xsd:enumeration value="outsideMargin"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PosV">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="align" type="ST_AlignV" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="posOffset" type="ST_PositionOffset" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
    <xsd:attribute name="relativeFrom" type="ST_RelFromV" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Anchor">
    <xsd:sequence>
      <xsd:element name="simplePos" type="a:CT_Point2D"/>
      <xsd:element name="positionH" type="CT_PosH"/>
      <xsd:element name="positionV" type="CT_PosV"/>
      <xsd:element name="extent" type="a:CT_PositiveSize2D"/>
      <xsd:element name="effectExtent" type="CT_EffectExtent" minOccurs="0"/>
      <xsd:group ref="EG_WrapType"/>
      <xsd:element name="docPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"
        minOccurs="0" maxOccurs="1"/>
      <xsd:element ref="a:graphic" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="distT" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distB" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distL" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="distR" type="ST_WrapDistance" use="optional"/>
    <xsd:attribute name="simplePos" type="xsd:boolean"/>
    <xsd:attribute name="relativeHeight" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="behindDoc" type="xsd:boolean" use="required"/>
    <xsd:attribute name="locked" type="xsd:boolean" use="required"/>
    <xsd:attribute name="layoutInCell" type="xsd:boolean" use="required"/>
    <xsd:attribute name="hidden" type="xsd:boolean" use="optional"/>
    <xsd:attribute name="allowOverlap" type="xsd:boolean" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TxbxContent">
    <xsd:group ref="w:EG_BlockLevelElts" minOccurs="1" maxOccurs="unbounded"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TextboxInfo">
    <xsd:sequence>
      <xsd:element name="txbxContent" type="CT_TxbxContent" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:unsignedShort" use="optional" default="0"/>
  </xsd:complexType>
  <xsd:complexType name="CT_LinkedTextboxInformation">
    <xsd:sequence>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:unsignedShort" use="required"/>
    <xsd:attribute name="seq" type="xsd:unsignedShort" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WordprocessingShape">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="0" maxOccurs="1"/>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="cNvSpPr" type="a:CT_NonVisualDrawingShapeProps" minOccurs="1"
          maxOccurs="1"/>
        <xsd:element name="cNvCnPr" type="a:CT_NonVisualConnectorProperties" minOccurs="1"
          maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
      <xsd:choice minOccurs="0" maxOccurs="1">
        <xsd:element name="txbx" type="CT_TextboxInfo" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="linkedTxbx" type="CT_LinkedTextboxInformation" minOccurs="1"
          maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="bodyPr" type="a:CT_TextBodyProperties" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="normalEastAsianFlow" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicFrame">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvFrPr" type="a:CT_NonVisualGraphicFrameProperties" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="xfrm" type="a:CT_Transform2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element ref="a:graphic" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_WordprocessingContentPartNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cNvContentPartPr" type="a:CT_NonVisualContentPartProperties" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_WordprocessingContentPart">
    <xsd:sequence>
      <xsd:element name="nvContentPartPr" type="CT_WordprocessingContentPartNonVisual" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="xfrm" type="a:CT_Transform2D" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="bwMode" type="a:ST_BlackWhiteMode" use="optional"/>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WordprocessingGroup">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cNvGrpSpPr" type="a:CT_NonVisualGroupDrawingShapeProps" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="grpSpPr" type="a:CT_GroupShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:choice minOccurs="0" maxOccurs="unbounded">
        <xsd:element ref="wsp"/>
        <xsd:element name="grpSp" type="CT_WordprocessingGroup"/>
        <xsd:element name="graphicFrame" type="CT_GraphicFrame"/>
        <xsd:element ref="dpct:pic"/>
        <xsd:element name="contentPart" type="CT_WordprocessingContentPart"/>
      </xsd:choice>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_WordprocessingCanvas">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="bg" type="a:CT_BackgroundFormatting" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="whole" type="a:CT_WholeE2oFormatting" minOccurs="0" maxOccurs="1"/>
      <xsd:choice minOccurs="0" maxOccurs="unbounded">
        <xsd:element ref="wsp"/>
        <xsd:element ref="dpct:pic"/>
        <xsd:element name="contentPart" type="CT_WordprocessingContentPart"/>
        <xsd:element ref="wgp"/>
        <xsd:element name="graphicFrame" type="CT_GraphicFrame"/>
      </xsd:choice>
      <xsd:element name="extLst" type="a:CT_OfficeArtExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="wpc" type="CT_WordprocessingCanvas"/>
  <xsd:element name="wgp" type="CT_WordprocessingGroup"/>
  <xsd:element name="wsp" type="CT_WordprocessingShape"/>
  <xsd:element name="inline" type="CT_Inline"/>
  <xsd:element name="anchor" type="CT_Anchor"/>
</xsd:schema>
```
