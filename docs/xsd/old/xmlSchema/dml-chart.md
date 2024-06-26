# dml-chart.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main"
  xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
  xmlns="http://schemas.openxmlformats.org/drawingml/2006/chart"
  xmlns:cdr="http://schemas.openxmlformats.org/drawingml/2006/chartDrawing"
  xmlns:s="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
  targetNamespace="http://schemas.openxmlformats.org/drawingml/2006/chart"
  elementFormDefault="qualified" attributeFormDefault="unqualified" blockDefault="#all">
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    schemaLocation="shared-relationshipReference.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/main"
    schemaLocation="dml-main.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/chartDrawing"
    schemaLocation="dml-chartDrawing.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
    schemaLocation="shared-commonSimpleTypes.xsd"/>
  <xsd:complexType name="CT_Boolean">
    <xsd:attribute name="val" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Double">
    <xsd:attribute name="val" type="xsd:double" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_UnsignedInt">
    <xsd:attribute name="val" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_RelId">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Extension">
    <xsd:sequence>
      <xsd:any processContents="lax"/>
    </xsd:sequence>
    <xsd:attribute name="uri" type="xsd:token"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ExtensionList">
    <xsd:sequence>
      <xsd:element name="ext" type="CT_Extension" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_NumVal">
    <xsd:sequence>
      <xsd:element name="v" type="s:ST_Xstring" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="idx" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="formatCode" type="s:ST_Xstring" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_NumData">
    <xsd:sequence>
      <xsd:element name="formatCode" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ptCount" type="CT_UnsignedInt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pt" type="CT_NumVal" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_NumRef">
    <xsd:sequence>
      <xsd:element name="f" type="xsd:string" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="numCache" type="CT_NumData" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_NumDataSource">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="numRef" type="CT_NumRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="numLit" type="CT_NumData" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_StrVal">
    <xsd:sequence>
      <xsd:element name="v" type="s:ST_Xstring" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="idx" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_StrData">
    <xsd:sequence>
      <xsd:element name="ptCount" type="CT_UnsignedInt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pt" type="CT_StrVal" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_StrRef">
    <xsd:sequence>
      <xsd:element name="f" type="xsd:string" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="strCache" type="CT_StrData" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Tx">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="strRef" type="CT_StrRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="rich" type="a:CT_TextBody" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_TextLanguageID">
    <xsd:attribute name="val" type="s:ST_Lang" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Lvl">
    <xsd:sequence>
      <xsd:element name="pt" type="CT_StrVal" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_MultiLvlStrData">
    <xsd:sequence>
      <xsd:element name="ptCount" type="CT_UnsignedInt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="lvl" type="CT_Lvl" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_MultiLvlStrRef">
    <xsd:sequence>
      <xsd:element name="f" type="xsd:string" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="multiLvlStrCache" type="CT_MultiLvlStrData" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_AxDataSource">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="multiLvlStrRef" type="CT_MultiLvlStrRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="numRef" type="CT_NumRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="numLit" type="CT_NumData" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="strRef" type="CT_StrRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="strLit" type="CT_StrData" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SerTx">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="strRef" type="CT_StrRef" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="v" type="s:ST_Xstring" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_LayoutTarget">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="inner"/>
      <xsd:enumeration value="outer"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LayoutTarget">
    <xsd:attribute name="val" type="ST_LayoutTarget" default="outer"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_LayoutMode">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="edge"/>
      <xsd:enumeration value="factor"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LayoutMode">
    <xsd:attribute name="val" type="ST_LayoutMode" default="factor"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ManualLayout">
    <xsd:sequence>
      <xsd:element name="layoutTarget" type="CT_LayoutTarget" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="xMode" type="CT_LayoutMode" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="yMode" type="CT_LayoutMode" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="wMode" type="CT_LayoutMode" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="hMode" type="CT_LayoutMode" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="x" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="y" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="w" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="h" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Layout">
    <xsd:sequence>
      <xsd:element name="manualLayout" type="CT_ManualLayout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Title">
    <xsd:sequence>
      <xsd:element name="tx" type="CT_Tx" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="overlay" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_RotX">
    <xsd:restriction base="xsd:byte">
      <xsd:minInclusive value="-90"/>
      <xsd:maxInclusive value="90"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_RotX">
    <xsd:attribute name="val" type="ST_RotX" default="0"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_HPercent">
    <xsd:union memberTypes="ST_HPercentWithSymbol ST_HPercentUShort"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_HPercentWithSymbol">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([5-9])|([1-9][0-9])|([1-4][0-9][0-9])|500)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_HPercentUShort">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="5"/>
      <xsd:maxInclusive value="500"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_HPercent">
    <xsd:attribute name="val" type="ST_HPercent" default="100%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_RotY">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="360"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_RotY">
    <xsd:attribute name="val" type="ST_RotY" default="0"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_DepthPercent">
    <xsd:union memberTypes="ST_DepthPercentWithSymbol ST_DepthPercentUShort"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_DepthPercentWithSymbol">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([2-9][0-9])|([1-9][0-9][0-9])|(1[0-9][0-9][0-9])|2000)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_DepthPercentUShort">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="20"/>
      <xsd:maxInclusive value="2000"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_DepthPercent">
    <xsd:attribute name="val" type="ST_DepthPercent" default="100%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Perspective">
    <xsd:restriction base="xsd:unsignedByte">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="240"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Perspective">
    <xsd:attribute name="val" type="ST_Perspective" default="30"/>
  </xsd:complexType>
  <xsd:complexType name="CT_View3D">
    <xsd:sequence>
      <xsd:element name="rotX" type="CT_RotX" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="hPercent" type="CT_HPercent" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="rotY" type="CT_RotY" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="depthPercent" type="CT_DepthPercent" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="rAngAx" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="perspective" type="CT_Perspective" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Surface">
    <xsd:sequence>
      <xsd:element name="thickness" type="CT_Thickness" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pictureOptions" type="CT_PictureOptions" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_Thickness">
    <xsd:union memberTypes="ST_ThicknessPercent xsd:unsignedInt"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_ThicknessPercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="([0-9]+)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Thickness">
    <xsd:attribute name="val" type="ST_Thickness" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_DTable">
    <xsd:sequence>
      <xsd:element name="showHorzBorder" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showVertBorder" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showOutline" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showKeys" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_GapAmount">
    <xsd:union memberTypes="ST_GapAmountPercent ST_GapAmountUShort"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_GapAmountPercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([0-9])|([1-9][0-9])|([1-4][0-9][0-9])|500)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_GapAmountUShort">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="500"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_GapAmount">
    <xsd:attribute name="val" type="ST_GapAmount" default="150%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Overlap">
    <xsd:union memberTypes="ST_OverlapPercent ST_OverlapByte"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_OverlapPercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="(-?0*(([0-9])|([1-9][0-9])|100))%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_OverlapByte">
    <xsd:restriction base="xsd:byte">
      <xsd:minInclusive value="-100"/>
      <xsd:maxInclusive value="100"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Overlap">
    <xsd:attribute name="val" type="ST_Overlap" default="0%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_BubbleScale">
    <xsd:union memberTypes="ST_BubbleScalePercent ST_BubbleScaleUInt"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_BubbleScalePercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([0-9])|([1-9][0-9])|([1-2][0-9][0-9])|300)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_BubbleScaleUInt">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="300"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_BubbleScale">
    <xsd:attribute name="val" type="ST_BubbleScale" default="100%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_SizeRepresents">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="area"/>
      <xsd:enumeration value="w"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SizeRepresents">
    <xsd:attribute name="val" type="ST_SizeRepresents" default="area"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_FirstSliceAng">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="360"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_FirstSliceAng">
    <xsd:attribute name="val" type="ST_FirstSliceAng" default="0"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_HoleSize">
    <xsd:union memberTypes="ST_HoleSizePercent ST_HoleSizeUByte"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_HoleSizePercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*([1-9]|([1-8][0-9])|90)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_HoleSizeUByte">
    <xsd:restriction base="xsd:unsignedByte">
      <xsd:minInclusive value="1"/>
      <xsd:maxInclusive value="90"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_HoleSize">
    <xsd:attribute name="val" type="ST_HoleSize" default="10%"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_SplitType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="auto"/>
      <xsd:enumeration value="cust"/>
      <xsd:enumeration value="percent"/>
      <xsd:enumeration value="pos"/>
      <xsd:enumeration value="val"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SplitType">
    <xsd:attribute name="val" type="ST_SplitType" default="auto"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CustSplit">
    <xsd:sequence>
      <xsd:element name="secondPiePt" type="CT_UnsignedInt" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_SecondPieSize">
    <xsd:union memberTypes="ST_SecondPieSizePercent ST_SecondPieSizeUShort"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_SecondPieSizePercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([5-9])|([1-9][0-9])|(1[0-9][0-9])|200)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_SecondPieSizeUShort">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="5"/>
      <xsd:maxInclusive value="200"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SecondPieSize">
    <xsd:attribute name="val" type="ST_SecondPieSize" default="75%"/>
  </xsd:complexType>
  <xsd:complexType name="CT_NumFmt">
    <xsd:attribute name="formatCode" type="s:ST_Xstring" use="required"/>
    <xsd:attribute name="sourceLinked" type="xsd:boolean"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_LblAlgn">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="ctr"/>
      <xsd:enumeration value="l"/>
      <xsd:enumeration value="r"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LblAlgn">
    <xsd:attribute name="val" type="ST_LblAlgn" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_DLblPos">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="bestFit"/>
      <xsd:enumeration value="b"/>
      <xsd:enumeration value="ctr"/>
      <xsd:enumeration value="inBase"/>
      <xsd:enumeration value="inEnd"/>
      <xsd:enumeration value="l"/>
      <xsd:enumeration value="outEnd"/>
      <xsd:enumeration value="r"/>
      <xsd:enumeration value="t"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_DLblPos">
    <xsd:attribute name="val" type="ST_DLblPos" use="required"/>
  </xsd:complexType>
  <xsd:group name="EG_DLblShared">
    <xsd:sequence>
      <xsd:element name="numFmt" type="CT_NumFmt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dLblPos" type="CT_DLblPos" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showLegendKey" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showVal" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showCatName" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showSerName" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showPercent" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showBubbleSize" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="separator" type="xsd:string" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:group name="Group_DLbl">
    <xsd:sequence>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tx" type="CT_Tx" minOccurs="0" maxOccurs="1"/>
      <xsd:group ref="EG_DLblShared" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_DLbl">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:choice>
        <xsd:element name="delete" type="CT_Boolean" minOccurs="1" maxOccurs="1"/>
        <xsd:group ref="Group_DLbl" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="Group_DLbls">
    <xsd:sequence>
      <xsd:group ref="EG_DLblShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="showLeaderLines" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="leaderLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_DLbls">
    <xsd:sequence>
      <xsd:element name="dLbl" type="CT_DLbl" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:choice>
        <xsd:element name="delete" type="CT_Boolean" minOccurs="1" maxOccurs="1"/>
        <xsd:group ref="Group_DLbls" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_MarkerStyle">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="circle"/>
      <xsd:enumeration value="dash"/>
      <xsd:enumeration value="diamond"/>
      <xsd:enumeration value="dot"/>
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="picture"/>
      <xsd:enumeration value="plus"/>
      <xsd:enumeration value="square"/>
      <xsd:enumeration value="star"/>
      <xsd:enumeration value="triangle"/>
      <xsd:enumeration value="x"/>
      <xsd:enumeration value="auto"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_MarkerStyle">
    <xsd:attribute name="val" type="ST_MarkerStyle" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_MarkerSize">
    <xsd:restriction base="xsd:unsignedByte">
      <xsd:minInclusive value="2"/>
      <xsd:maxInclusive value="72"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_MarkerSize">
    <xsd:attribute name="val" type="ST_MarkerSize" default="5"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Marker">
    <xsd:sequence>
      <xsd:element name="symbol" type="CT_MarkerStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="size" type="CT_MarkerSize" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DPt">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="invertIfNegative" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Marker" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bubble3D" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="explosion" type="CT_UnsignedInt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pictureOptions" type="CT_PictureOptions" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_TrendlineType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="exp"/>
      <xsd:enumeration value="linear"/>
      <xsd:enumeration value="log"/>
      <xsd:enumeration value="movingAvg"/>
      <xsd:enumeration value="poly"/>
      <xsd:enumeration value="power"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TrendlineType">
    <xsd:attribute name="val" type="ST_TrendlineType" default="linear"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Order">
    <xsd:restriction base="xsd:unsignedByte">
      <xsd:minInclusive value="2"/>
      <xsd:maxInclusive value="6"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Order">
    <xsd:attribute name="val" type="ST_Order" default="2"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Period">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="2"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Period">
    <xsd:attribute name="val" type="ST_Period" default="2"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TrendlineLbl">
    <xsd:sequence>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tx" type="CT_Tx" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="numFmt" type="CT_NumFmt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Trendline">
    <xsd:sequence>
      <xsd:element name="name" type="xsd:string" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendlineType" type="CT_TrendlineType" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="order" type="CT_Order" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="period" type="CT_Period" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="forward" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="backward" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="intercept" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dispRSqr" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dispEq" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendlineLbl" type="CT_TrendlineLbl" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_ErrDir">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="x"/>
      <xsd:enumeration value="y"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ErrDir">
    <xsd:attribute name="val" type="ST_ErrDir" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_ErrBarType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="both"/>
      <xsd:enumeration value="minus"/>
      <xsd:enumeration value="plus"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ErrBarType">
    <xsd:attribute name="val" type="ST_ErrBarType" default="both"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_ErrValType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="cust"/>
      <xsd:enumeration value="fixedVal"/>
      <xsd:enumeration value="percentage"/>
      <xsd:enumeration value="stdDev"/>
      <xsd:enumeration value="stdErr"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ErrValType">
    <xsd:attribute name="val" type="ST_ErrValType" default="fixedVal"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ErrBars">
    <xsd:sequence>
      <xsd:element name="errDir" type="CT_ErrDir" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="errBarType" type="CT_ErrBarType" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="errValType" type="CT_ErrValType" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="noEndCap" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="plus" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minus" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_UpDownBar">
    <xsd:sequence>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_UpDownBars">
    <xsd:sequence>
      <xsd:element name="gapWidth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="upBars" type="CT_UpDownBar" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="downBars" type="CT_UpDownBar" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_SerShared">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="order" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tx" type="CT_SerTx" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_LineSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Marker" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendline" type="CT_Trendline" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="errBars" type="CT_ErrBars" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="smooth" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_ScatterSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Marker" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendline" type="CT_Trendline" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="errBars" type="CT_ErrBars" minOccurs="0" maxOccurs="2"/>
      <xsd:element name="xVal" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="yVal" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="smooth" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_RadarSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Marker" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_BarSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="invertIfNegative" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pictureOptions" type="CT_PictureOptions" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendline" type="CT_Trendline" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="errBars" type="CT_ErrBars" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_AreaSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="pictureOptions" type="CT_PictureOptions" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendline" type="CT_Trendline" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="errBars" type="CT_ErrBars" minOccurs="0" maxOccurs="2"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_PieSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="explosion" type="CT_UnsignedInt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_BubbleSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="invertIfNegative" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dPt" type="CT_DPt" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="trendline" type="CT_Trendline" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="errBars" type="CT_ErrBars" minOccurs="0" maxOccurs="2"/>
      <xsd:element name="xVal" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="yVal" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bubbleSize" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bubble3D" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SurfaceSer">
    <xsd:sequence>
      <xsd:group ref="EG_SerShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cat" type="CT_AxDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="val" type="CT_NumDataSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_Grouping">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="percentStacked"/>
      <xsd:enumeration value="standard"/>
      <xsd:enumeration value="stacked"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Grouping">
    <xsd:attribute name="val" type="ST_Grouping" default="standard"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ChartLines">
    <xsd:sequence>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_LineChartShared">
    <xsd:sequence>
      <xsd:element name="grouping" type="CT_Grouping" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_LineSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dropLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_LineChart">
    <xsd:sequence>
      <xsd:group ref="EG_LineChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hiLowLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="upDownBars" type="CT_UpDownBars" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="smooth" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Line3DChart">
    <xsd:sequence>
      <xsd:group ref="EG_LineChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gapDepth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="3" maxOccurs="3"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_StockChart">
    <xsd:sequence>
      <xsd:element name="ser" type="CT_LineSer" minOccurs="3" maxOccurs="4"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dropLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="hiLowLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="upDownBars" type="CT_UpDownBars" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_ScatterStyle">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="line"/>
      <xsd:enumeration value="lineMarker"/>
      <xsd:enumeration value="marker"/>
      <xsd:enumeration value="smooth"/>
      <xsd:enumeration value="smoothMarker"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ScatterStyle">
    <xsd:attribute name="val" type="ST_ScatterStyle" default="marker"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ScatterChart">
    <xsd:sequence>
      <xsd:element name="scatterStyle" type="CT_ScatterStyle" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_ScatterSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_RadarStyle">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="standard"/>
      <xsd:enumeration value="marker"/>
      <xsd:enumeration value="filled"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_RadarStyle">
    <xsd:attribute name="val" type="ST_RadarStyle" default="standard"/>
  </xsd:complexType>
  <xsd:complexType name="CT_RadarChart">
    <xsd:sequence>
      <xsd:element name="radarStyle" type="CT_RadarStyle" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_RadarSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_BarGrouping">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="percentStacked"/>
      <xsd:enumeration value="clustered"/>
      <xsd:enumeration value="standard"/>
      <xsd:enumeration value="stacked"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_BarGrouping">
    <xsd:attribute name="val" type="ST_BarGrouping" default="clustered"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_BarDir">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="bar"/>
      <xsd:enumeration value="col"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_BarDir">
    <xsd:attribute name="val" type="ST_BarDir" default="col"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Shape">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="cone"/>
      <xsd:enumeration value="coneToMax"/>
      <xsd:enumeration value="box"/>
      <xsd:enumeration value="cylinder"/>
      <xsd:enumeration value="pyramid"/>
      <xsd:enumeration value="pyramidToMax"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Shape">
    <xsd:attribute name="val" type="ST_Shape" default="box"/>
  </xsd:complexType>
  <xsd:group name="EG_BarChartShared">
    <xsd:sequence>
      <xsd:element name="barDir" type="CT_BarDir" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="grouping" type="CT_BarGrouping" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_BarSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_BarChart">
    <xsd:sequence>
      <xsd:group ref="EG_BarChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gapWidth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="overlap" type="CT_Overlap" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="serLines" type="CT_ChartLines" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Bar3DChart">
    <xsd:sequence>
      <xsd:group ref="EG_BarChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gapWidth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="gapDepth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="shape" type="CT_Shape" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="3"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_AreaChartShared">
    <xsd:sequence>
      <xsd:element name="grouping" type="CT_Grouping" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_AreaSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dropLines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_AreaChart">
    <xsd:sequence>
      <xsd:group ref="EG_AreaChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Area3DChart">
    <xsd:sequence>
      <xsd:group ref="EG_AreaChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gapDepth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="3"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_PieChartShared">
    <xsd:sequence>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_PieSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_PieChart">
    <xsd:sequence>
      <xsd:group ref="EG_PieChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="firstSliceAng" type="CT_FirstSliceAng" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Pie3DChart">
    <xsd:sequence>
      <xsd:group ref="EG_PieChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DoughnutChart">
    <xsd:sequence>
      <xsd:group ref="EG_PieChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="firstSliceAng" type="CT_FirstSliceAng" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="holeSize" type="CT_HoleSize" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_OfPieType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="pie"/>
      <xsd:enumeration value="bar"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_OfPieType">
    <xsd:attribute name="val" type="ST_OfPieType" default="pie"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OfPieChart">
    <xsd:sequence>
      <xsd:element name="ofPieType" type="CT_OfPieType" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_PieChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="gapWidth" type="CT_GapAmount" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="splitType" type="CT_SplitType" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="splitPos" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="custSplit" type="CT_CustSplit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="secondPieSize" type="CT_SecondPieSize" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="serLines" type="CT_ChartLines" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_BubbleChart">
    <xsd:sequence>
      <xsd:element name="varyColors" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_BubbleSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="dLbls" type="CT_DLbls" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bubble3D" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bubbleScale" type="CT_BubbleScale" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showNegBubbles" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="sizeRepresents" type="CT_SizeRepresents" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="2"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_BandFmt">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_BandFmts">
    <xsd:sequence>
      <xsd:element name="bandFmt" type="CT_BandFmt" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:group name="EG_SurfaceChartShared">
    <xsd:sequence>
      <xsd:element name="wireframe" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="ser" type="CT_SurfaceSer" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="bandFmts" type="CT_BandFmts" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_SurfaceChart">
    <xsd:sequence>
      <xsd:group ref="EG_SurfaceChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="2" maxOccurs="3"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Surface3DChart">
    <xsd:sequence>
      <xsd:group ref="EG_SurfaceChartShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="3" maxOccurs="3"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_AxPos">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="b"/>
      <xsd:enumeration value="l"/>
      <xsd:enumeration value="r"/>
      <xsd:enumeration value="t"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_AxPos">
    <xsd:attribute name="val" type="ST_AxPos" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Crosses">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="autoZero"/>
      <xsd:enumeration value="max"/>
      <xsd:enumeration value="min"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Crosses">
    <xsd:attribute name="val" type="ST_Crosses" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_CrossBetween">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="between"/>
      <xsd:enumeration value="midCat"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_CrossBetween">
    <xsd:attribute name="val" type="ST_CrossBetween" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TickMark">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="cross"/>
      <xsd:enumeration value="in"/>
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="out"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TickMark">
    <xsd:attribute name="val" type="ST_TickMark" default="cross"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TickLblPos">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="high"/>
      <xsd:enumeration value="low"/>
      <xsd:enumeration value="nextTo"/>
      <xsd:enumeration value="none"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TickLblPos">
    <xsd:attribute name="val" type="ST_TickLblPos" default="nextTo"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_Skip">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="1"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Skip">
    <xsd:attribute name="val" type="ST_Skip" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TimeUnit">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="days"/>
      <xsd:enumeration value="months"/>
      <xsd:enumeration value="years"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TimeUnit">
    <xsd:attribute name="val" type="ST_TimeUnit" default="days"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_AxisUnit">
    <xsd:restriction base="xsd:double">
      <xsd:minExclusive value="0"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_AxisUnit">
    <xsd:attribute name="val" type="ST_AxisUnit" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_BuiltInUnit">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="hundreds"/>
      <xsd:enumeration value="thousands"/>
      <xsd:enumeration value="tenThousands"/>
      <xsd:enumeration value="hundredThousands"/>
      <xsd:enumeration value="millions"/>
      <xsd:enumeration value="tenMillions"/>
      <xsd:enumeration value="hundredMillions"/>
      <xsd:enumeration value="billions"/>
      <xsd:enumeration value="trillions"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_BuiltInUnit">
    <xsd:attribute name="val" type="ST_BuiltInUnit" default="thousands"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_PictureFormat">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="stretch"/>
      <xsd:enumeration value="stack"/>
      <xsd:enumeration value="stackScale"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PictureFormat">
    <xsd:attribute name="val" type="ST_PictureFormat" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_PictureStackUnit">
    <xsd:restriction base="xsd:double">
      <xsd:minExclusive value="0"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PictureStackUnit">
    <xsd:attribute name="val" type="ST_PictureStackUnit" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PictureOptions">
    <xsd:sequence>
      <xsd:element name="applyToFront" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="applyToSides" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="applyToEnd" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pictureFormat" type="CT_PictureFormat" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pictureStackUnit" type="CT_PictureStackUnit" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DispUnitsLbl">
    <xsd:sequence>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tx" type="CT_Tx" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DispUnits">
    <xsd:sequence>
      <xsd:choice>
        <xsd:element name="custUnit" type="CT_Double" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="builtInUnit" type="CT_BuiltInUnit" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="dispUnitsLbl" type="CT_DispUnitsLbl" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_Orientation">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="maxMin"/>
      <xsd:enumeration value="minMax"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Orientation">
    <xsd:attribute name="val" type="ST_Orientation" default="minMax"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_LogBase">
    <xsd:restriction base="xsd:double">
      <xsd:minInclusive value="2"/>
      <xsd:maxInclusive value="1000"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LogBase">
    <xsd:attribute name="val" type="ST_LogBase" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Scaling">
    <xsd:sequence>
      <xsd:element name="logBase" type="CT_LogBase" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="orientation" type="CT_Orientation" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="max" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="min" type="CT_Double" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_LblOffset">
    <xsd:union memberTypes="ST_LblOffsetPercent ST_LblOffsetUShort"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_LblOffsetPercent">
    <xsd:restriction base="xsd:string">
      <xsd:pattern value="0*(([0-9])|([1-9][0-9])|([1-9][0-9][0-9])|1000)%"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_LblOffsetUShort">
    <xsd:restriction base="xsd:unsignedShort">
      <xsd:minInclusive value="0"/>
      <xsd:maxInclusive value="1000"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LblOffset">
    <xsd:attribute name="val" type="ST_LblOffset" default="100%"/>
  </xsd:complexType>
  <xsd:group name="EG_AxShared">
    <xsd:sequence>
      <xsd:element name="axId" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="scaling" type="CT_Scaling" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="delete" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="axPos" type="CT_AxPos" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="majorGridlines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minorGridlines" type="CT_ChartLines" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="title" type="CT_Title" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="numFmt" type="CT_NumFmt" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="majorTickMark" type="CT_TickMark" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minorTickMark" type="CT_TickMark" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tickLblPos" type="CT_TickLblPos" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="crossAx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:choice minOccurs="0" maxOccurs="1">
        <xsd:element name="crosses" type="CT_Crosses" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="crossesAt" type="CT_Double" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_CatAx">
    <xsd:sequence>
      <xsd:group ref="EG_AxShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="auto" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="lblAlgn" type="CT_LblAlgn" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="lblOffset" type="CT_LblOffset" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tickLblSkip" type="CT_Skip" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tickMarkSkip" type="CT_Skip" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="noMultiLvlLbl" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DateAx">
    <xsd:sequence>
      <xsd:group ref="EG_AxShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="auto" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="lblOffset" type="CT_LblOffset" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="baseTimeUnit" type="CT_TimeUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="majorUnit" type="CT_AxisUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="majorTimeUnit" type="CT_TimeUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minorUnit" type="CT_AxisUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minorTimeUnit" type="CT_TimeUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SerAx">
    <xsd:sequence>
      <xsd:group ref="EG_AxShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tickLblSkip" type="CT_Skip" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="tickMarkSkip" type="CT_Skip" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_ValAx">
    <xsd:sequence>
      <xsd:group ref="EG_AxShared" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="crossBetween" type="CT_CrossBetween" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="majorUnit" type="CT_AxisUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="minorUnit" type="CT_AxisUnit" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dispUnits" type="CT_DispUnits" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_PlotArea">
    <xsd:sequence>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:choice minOccurs="1" maxOccurs="unbounded">
        <xsd:element name="areaChart" type="CT_AreaChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="area3DChart" type="CT_Area3DChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="lineChart" type="CT_LineChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="line3DChart" type="CT_Line3DChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="stockChart" type="CT_StockChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="radarChart" type="CT_RadarChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="scatterChart" type="CT_ScatterChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="pieChart" type="CT_PieChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="pie3DChart" type="CT_Pie3DChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="doughnutChart" type="CT_DoughnutChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="barChart" type="CT_BarChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="bar3DChart" type="CT_Bar3DChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="ofPieChart" type="CT_OfPieChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="surfaceChart" type="CT_SurfaceChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="surface3DChart" type="CT_Surface3DChart" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="bubbleChart" type="CT_BubbleChart" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:choice minOccurs="0" maxOccurs="unbounded">
        <xsd:element name="valAx" type="CT_ValAx" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="catAx" type="CT_CatAx" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="dateAx" type="CT_DateAx" minOccurs="1" maxOccurs="1"/>
        <xsd:element name="serAx" type="CT_SerAx" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="dTable" type="CT_DTable" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_PivotFmt">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="marker" type="CT_Marker" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dLbl" type="CT_DLbl" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_PivotFmts">
    <xsd:sequence>
      <xsd:element name="pivotFmt" type="CT_PivotFmt" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_LegendPos">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="b"/>
      <xsd:enumeration value="tr"/>
      <xsd:enumeration value="l"/>
      <xsd:enumeration value="r"/>
      <xsd:enumeration value="t"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_LegendPos">
    <xsd:attribute name="val" type="ST_LegendPos" default="r"/>
  </xsd:complexType>
  <xsd:group name="EG_LegendEntryData">
    <xsd:sequence>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_LegendEntry">
    <xsd:sequence>
      <xsd:element name="idx" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:choice>
        <xsd:element name="delete" type="CT_Boolean" minOccurs="1" maxOccurs="1"/>
        <xsd:group ref="EG_LegendEntryData" minOccurs="1" maxOccurs="1"/>
      </xsd:choice>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Legend">
    <xsd:sequence>
      <xsd:element name="legendPos" type="CT_LegendPos" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="legendEntry" type="CT_LegendEntry" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="layout" type="CT_Layout" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="overlay" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_DispBlanksAs">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="span"/>
      <xsd:enumeration value="gap"/>
      <xsd:enumeration value="zero"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_DispBlanksAs">
    <xsd:attribute name="val" type="ST_DispBlanksAs" default="zero"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Chart">
    <xsd:sequence>
      <xsd:element name="title" type="CT_Title" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="autoTitleDeleted" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pivotFmts" type="CT_PivotFmts" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="view3D" type="CT_View3D" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="floor" type="CT_Surface" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="sideWall" type="CT_Surface" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="backWall" type="CT_Surface" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="plotArea" type="CT_PlotArea" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="legend" type="CT_Legend" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="plotVisOnly" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="dispBlanksAs" type="CT_DispBlanksAs" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showDLblsOverMax" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_Style">
    <xsd:restriction base="xsd:unsignedByte">
      <xsd:minInclusive value="1"/>
      <xsd:maxInclusive value="48"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Style">
    <xsd:attribute name="val" type="ST_Style" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PivotSource">
    <xsd:sequence>
      <xsd:element name="name" type="s:ST_Xstring" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="fmtId" type="CT_UnsignedInt" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Protection">
    <xsd:sequence>
      <xsd:element name="chartObject" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="data" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="formatting" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="selection" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="userInterface" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_HeaderFooter">
    <xsd:sequence>
      <xsd:element name="oddHeader" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="oddFooter" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="evenHeader" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="evenFooter" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="firstHeader" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="firstFooter" type="s:ST_Xstring" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="alignWithMargins" type="xsd:boolean" default="true"/>
    <xsd:attribute name="differentOddEven" type="xsd:boolean" default="false"/>
    <xsd:attribute name="differentFirst" type="xsd:boolean" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PageMargins">
    <xsd:attribute name="l" type="xsd:double" use="required"/>
    <xsd:attribute name="r" type="xsd:double" use="required"/>
    <xsd:attribute name="t" type="xsd:double" use="required"/>
    <xsd:attribute name="b" type="xsd:double" use="required"/>
    <xsd:attribute name="header" type="xsd:double" use="required"/>
    <xsd:attribute name="footer" type="xsd:double" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_PageSetupOrientation">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="default"/>
      <xsd:enumeration value="portrait"/>
      <xsd:enumeration value="landscape"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ExternalData">
    <xsd:sequence>
      <xsd:element name="autoUpdate" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PageSetup">
    <xsd:attribute name="paperSize" type="xsd:unsignedInt" use="optional" default="1"/>
    <xsd:attribute name="paperHeight" type="s:ST_PositiveUniversalMeasure" use="optional"/>
    <xsd:attribute name="paperWidth" type="s:ST_PositiveUniversalMeasure" use="optional"/>
    <xsd:attribute name="firstPageNumber" type="xsd:unsignedInt" use="optional" default="1"/>
    <xsd:attribute name="orientation" type="ST_PageSetupOrientation" use="optional"
      default="default"/>
    <xsd:attribute name="blackAndWhite" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="draft" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="useFirstPageNumber" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="horizontalDpi" type="xsd:int" use="optional" default="600"/>
    <xsd:attribute name="verticalDpi" type="xsd:int" use="optional" default="600"/>
    <xsd:attribute name="copies" type="xsd:unsignedInt" use="optional" default="1"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PrintSettings">
    <xsd:sequence>
      <xsd:element name="headerFooter" type="CT_HeaderFooter" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pageMargins" type="CT_PageMargins" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pageSetup" type="CT_PageSetup" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="legacyDrawingHF" type="CT_RelId" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_ChartSpace">
    <xsd:sequence>
      <xsd:element name="date1904" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="lang" type="CT_TextLanguageID" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="roundedCorners" type="CT_Boolean" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="style" type="CT_Style" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="clrMapOvr" type="a:CT_ColorMapping" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pivotSource" type="CT_PivotSource" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="protection" type="CT_Protection" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="chart" type="CT_Chart" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txPr" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="externalData" type="CT_ExternalData" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="printSettings" type="CT_PrintSettings" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="userShapes" type="CT_RelId" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="chartSpace" type="CT_ChartSpace"/>
  <xsd:element name="userShapes" type="cdr:CT_Drawing"/>
  <xsd:element name="chart" type="CT_RelId"/>
</xsd:schema>
```
