# pml.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/presentationml/2006/main"
  xmlns:p="http://schemas.openxmlformats.org/presentationml/2006/main"
  xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main"
  xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
  xmlns:s="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
  elementFormDefault="qualified"
  targetNamespace="http://schemas.openxmlformats.org/presentationml/2006/main">
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    schemaLocation="shared-relationshipReference.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/drawingml/2006/main"
    schemaLocation="dml-main.xsd"/>
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
    schemaLocation="shared-commonSimpleTypes.xsd"/>
  <xsd:simpleType name="ST_TransitionSideDirectionType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="l"/>
      <xsd:enumeration value="u"/>
      <xsd:enumeration value="r"/>
      <xsd:enumeration value="d"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TransitionCornerDirectionType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="lu"/>
      <xsd:enumeration value="ru"/>
      <xsd:enumeration value="ld"/>
      <xsd:enumeration value="rd"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TransitionInOutDirectionType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="out"/>
      <xsd:enumeration value="in"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SideDirectionTransition">
    <xsd:attribute name="dir" type="ST_TransitionSideDirectionType" use="optional" default="l"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CornerDirectionTransition">
    <xsd:attribute name="dir" type="ST_TransitionCornerDirectionType" use="optional" default="lu"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TransitionEightDirectionType">
    <xsd:union memberTypes="ST_TransitionSideDirectionType ST_TransitionCornerDirectionType"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_EightDirectionTransition">
    <xsd:attribute name="dir" type="ST_TransitionEightDirectionType" use="optional" default="l"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OrientationTransition">
    <xsd:attribute name="dir" type="ST_Direction" use="optional" default="horz"/>
  </xsd:complexType>
  <xsd:complexType name="CT_InOutTransition">
    <xsd:attribute name="dir" type="ST_TransitionInOutDirectionType" use="optional" default="out"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OptionalBlackTransition">
    <xsd:attribute name="thruBlk" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SplitTransition">
    <xsd:attribute name="orient" type="ST_Direction" use="optional" default="horz"/>
    <xsd:attribute name="dir" type="ST_TransitionInOutDirectionType" use="optional" default="out"/>
  </xsd:complexType>
  <xsd:complexType name="CT_WheelTransition">
    <xsd:attribute name="spokes" type="xsd:unsignedInt" use="optional" default="4"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TransitionStartSoundAction">
    <xsd:sequence>
      <xsd:element minOccurs="1" maxOccurs="1" name="snd" type="a:CT_EmbeddedWAVAudioFile"/>
    </xsd:sequence>
    <xsd:attribute name="loop" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TransitionSoundAction">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="stSnd" type="CT_TransitionStartSoundAction"/>
      <xsd:element name="endSnd" type="CT_Empty"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:simpleType name="ST_TransitionSpeed">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="slow"/>
      <xsd:enumeration value="med"/>
      <xsd:enumeration value="fast"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideTransition">
    <xsd:sequence>
      <xsd:choice minOccurs="0" maxOccurs="1">
        <xsd:element name="blinds" type="CT_OrientationTransition"/>
        <xsd:element name="checker" type="CT_OrientationTransition"/>
        <xsd:element name="circle" type="CT_Empty"/>
        <xsd:element name="dissolve" type="CT_Empty"/>
        <xsd:element name="comb" type="CT_OrientationTransition"/>
        <xsd:element name="cover" type="CT_EightDirectionTransition"/>
        <xsd:element name="cut" type="CT_OptionalBlackTransition"/>
        <xsd:element name="diamond" type="CT_Empty"/>
        <xsd:element name="fade" type="CT_OptionalBlackTransition"/>
        <xsd:element name="newsflash" type="CT_Empty"/>
        <xsd:element name="plus" type="CT_Empty"/>
        <xsd:element name="pull" type="CT_EightDirectionTransition"/>
        <xsd:element name="push" type="CT_SideDirectionTransition"/>
        <xsd:element name="random" type="CT_Empty"/>
        <xsd:element name="randomBar" type="CT_OrientationTransition"/>
        <xsd:element name="split" type="CT_SplitTransition"/>
        <xsd:element name="strips" type="CT_CornerDirectionTransition"/>
        <xsd:element name="wedge" type="CT_Empty"/>
        <xsd:element name="wheel" type="CT_WheelTransition"/>
        <xsd:element name="wipe" type="CT_SideDirectionTransition"/>
        <xsd:element name="zoom" type="CT_InOutTransition"/>
      </xsd:choice>
      <xsd:element name="sndAc" minOccurs="0" maxOccurs="1" type="CT_TransitionSoundAction"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="spd" type="ST_TransitionSpeed" use="optional" default="fast"/>
    <xsd:attribute name="advClick" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="advTm" type="xsd:unsignedInt" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLTimeIndefinite">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="indefinite"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTime">
    <xsd:union memberTypes="xsd:unsignedInt ST_TLTimeIndefinite"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeID">
    <xsd:restriction base="xsd:unsignedInt"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLIterateIntervalTime">
    <xsd:attribute name="val" type="ST_TLTime" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLIterateIntervalPercentage">
    <xsd:attribute name="val" type="a:ST_PositivePercentage" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_IterateType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="el"/>
      <xsd:enumeration value="wd"/>
      <xsd:enumeration value="lt"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLIterateData">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="tmAbs" type="CT_TLIterateIntervalTime"/>
      <xsd:element name="tmPct" type="CT_TLIterateIntervalPercentage"/>
    </xsd:choice>
    <xsd:attribute name="type" type="ST_IterateType" use="optional" default="el"/>
    <xsd:attribute name="backwards" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLSubShapeId">
    <xsd:attribute name="spid" type="a:ST_ShapeID" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTextTargetElement">
    <xsd:choice minOccurs="0" maxOccurs="1">
      <xsd:element name="charRg" type="CT_IndexRange"/>
      <xsd:element name="pRg" type="CT_IndexRange"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLChartSubelementType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="gridLegend"/>
      <xsd:enumeration value="series"/>
      <xsd:enumeration value="category"/>
      <xsd:enumeration value="ptInSeries"/>
      <xsd:enumeration value="ptInCategory"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLOleChartTargetElement">
    <xsd:attribute name="type" type="ST_TLChartSubelementType" use="required"/>
    <xsd:attribute name="lvl" type="xsd:unsignedInt" use="optional" default="0"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLShapeTargetElement">
    <xsd:choice minOccurs="0" maxOccurs="1">
      <xsd:element name="bg" type="CT_Empty"/>
      <xsd:element name="subSp" type="CT_TLSubShapeId"/>
      <xsd:element name="oleChartEl" type="CT_TLOleChartTargetElement"/>
      <xsd:element name="txEl" type="CT_TLTextTargetElement"/>
      <xsd:element name="graphicEl" type="a:CT_AnimationElementChoice"/>
    </xsd:choice>
    <xsd:attribute name="spid" type="a:ST_DrawingElementId" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTimeTargetElement">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="sldTgt" type="CT_Empty"/>
      <xsd:element name="sndTgt" type="a:CT_EmbeddedWAVAudioFile"/>
      <xsd:element name="spTgt" type="CT_TLShapeTargetElement"/>
      <xsd:element name="inkTgt" type="CT_TLSubShapeId"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTriggerTimeNodeID">
    <xsd:attribute name="val" type="ST_TLTimeNodeID" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLTriggerRuntimeNode">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="first"/>
      <xsd:enumeration value="last"/>
      <xsd:enumeration value="all"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLTriggerRuntimeNode">
    <xsd:attribute name="val" type="ST_TLTriggerRuntimeNode" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLTriggerEvent">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="onBegin"/>
      <xsd:enumeration value="onEnd"/>
      <xsd:enumeration value="begin"/>
      <xsd:enumeration value="end"/>
      <xsd:enumeration value="onClick"/>
      <xsd:enumeration value="onDblClick"/>
      <xsd:enumeration value="onMouseOver"/>
      <xsd:enumeration value="onMouseOut"/>
      <xsd:enumeration value="onNext"/>
      <xsd:enumeration value="onPrev"/>
      <xsd:enumeration value="onStopAudio"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLTimeCondition">
    <xsd:choice minOccurs="0" maxOccurs="1">
      <xsd:element name="tgtEl" type="CT_TLTimeTargetElement"/>
      <xsd:element name="tn" type="CT_TLTriggerTimeNodeID"/>
      <xsd:element name="rtn" type="CT_TLTriggerRuntimeNode"/>
    </xsd:choice>
    <xsd:attribute name="evt" use="optional" type="ST_TLTriggerEvent"/>
    <xsd:attribute name="delay" type="ST_TLTime" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTimeConditionList">
    <xsd:sequence>
      <xsd:element name="cond" type="CT_TLTimeCondition" minOccurs="1" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_TimeNodeList">
    <xsd:choice minOccurs="1" maxOccurs="unbounded">
      <xsd:element name="par" type="CT_TLTimeNodeParallel"/>
      <xsd:element name="seq" type="CT_TLTimeNodeSequence"/>
      <xsd:element name="excl" type="CT_TLTimeNodeExclusive"/>
      <xsd:element name="anim" type="CT_TLAnimateBehavior"/>
      <xsd:element name="animClr" type="CT_TLAnimateColorBehavior"/>
      <xsd:element name="animEffect" type="CT_TLAnimateEffectBehavior"/>
      <xsd:element name="animMotion" type="CT_TLAnimateMotionBehavior"/>
      <xsd:element name="animRot" type="CT_TLAnimateRotationBehavior"/>
      <xsd:element name="animScale" type="CT_TLAnimateScaleBehavior"/>
      <xsd:element name="cmd" type="CT_TLCommandBehavior"/>
      <xsd:element name="set" type="CT_TLSetBehavior"/>
      <xsd:element name="audio" type="CT_TLMediaNodeAudio"/>
      <xsd:element name="video" type="CT_TLMediaNodeVideo"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLTimeNodePresetClassType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="entr"/>
      <xsd:enumeration value="exit"/>
      <xsd:enumeration value="emph"/>
      <xsd:enumeration value="path"/>
      <xsd:enumeration value="verb"/>
      <xsd:enumeration value="mediacall"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeRestartType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="always"/>
      <xsd:enumeration value="whenNotActive"/>
      <xsd:enumeration value="never"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeFillType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="remove"/>
      <xsd:enumeration value="freeze"/>
      <xsd:enumeration value="hold"/>
      <xsd:enumeration value="transition"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeSyncType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="canSlip"/>
      <xsd:enumeration value="locked"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeMasterRelation">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="sameClick"/>
      <xsd:enumeration value="lastClick"/>
      <xsd:enumeration value="nextClick"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLTimeNodeType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="clickEffect"/>
      <xsd:enumeration value="withEffect"/>
      <xsd:enumeration value="afterEffect"/>
      <xsd:enumeration value="mainSeq"/>
      <xsd:enumeration value="interactiveSeq"/>
      <xsd:enumeration value="clickPar"/>
      <xsd:enumeration value="withGroup"/>
      <xsd:enumeration value="afterGroup"/>
      <xsd:enumeration value="tmRoot"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLCommonTimeNodeData">
    <xsd:sequence>
      <xsd:element name="stCondLst" type="CT_TLTimeConditionList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="endCondLst" type="CT_TLTimeConditionList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="endSync" type="CT_TLTimeCondition" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="iterate" type="CT_TLIterateData" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="childTnLst" type="CT_TimeNodeList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="subTnLst" type="CT_TimeNodeList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="ST_TLTimeNodeID" use="optional"/>
    <xsd:attribute name="presetID" type="xsd:int" use="optional"/>
    <xsd:attribute name="presetClass" type="ST_TLTimeNodePresetClassType" use="optional"/>
    <xsd:attribute name="presetSubtype" type="xsd:int" use="optional"/>
    <xsd:attribute name="dur" type="ST_TLTime" use="optional"/>
    <xsd:attribute name="repeatCount" type="ST_TLTime" use="optional" default="1000"/>
    <xsd:attribute name="repeatDur" type="ST_TLTime" use="optional"/>
    <xsd:attribute name="spd" type="a:ST_Percentage" use="optional" default="100%"/>
    <xsd:attribute name="accel" type="a:ST_PositiveFixedPercentage" use="optional" default="0%"/>
    <xsd:attribute name="decel" type="a:ST_PositiveFixedPercentage" use="optional" default="0%"/>
    <xsd:attribute name="autoRev" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="restart" type="ST_TLTimeNodeRestartType" use="optional"/>
    <xsd:attribute name="fill" type="ST_TLTimeNodeFillType" use="optional"/>
    <xsd:attribute name="syncBehavior" type="ST_TLTimeNodeSyncType" use="optional"/>
    <xsd:attribute name="tmFilter" type="xsd:string" use="optional"/>
    <xsd:attribute name="evtFilter" type="xsd:string" use="optional"/>
    <xsd:attribute name="display" type="xsd:boolean" use="optional"/>
    <xsd:attribute name="masterRel" type="ST_TLTimeNodeMasterRelation" use="optional"/>
    <xsd:attribute name="bldLvl" type="xsd:int" use="optional"/>
    <xsd:attribute name="grpId" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="afterEffect" type="xsd:boolean" use="optional"/>
    <xsd:attribute name="nodeType" type="ST_TLTimeNodeType" use="optional"/>
    <xsd:attribute name="nodePh" type="xsd:boolean" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTimeNodeParallel">
    <xsd:sequence>
      <xsd:element name="cTn" type="CT_TLCommonTimeNodeData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLNextActionType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="seek"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLPreviousActionType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="skipTimed"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLTimeNodeSequence">
    <xsd:sequence>
      <xsd:element name="cTn" type="CT_TLCommonTimeNodeData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="prevCondLst" type="CT_TLTimeConditionList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="nextCondLst" type="CT_TLTimeConditionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="concurrent" type="xsd:boolean" use="optional"/>
    <xsd:attribute name="prevAc" type="ST_TLPreviousActionType" use="optional"/>
    <xsd:attribute name="nextAc" type="ST_TLNextActionType" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTimeNodeExclusive">
    <xsd:sequence>
      <xsd:element name="cTn" type="CT_TLCommonTimeNodeData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_TLBehaviorAttributeNameList">
    <xsd:sequence>
      <xsd:element name="attrName" type="xsd:string" minOccurs="1" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLBehaviorAdditiveType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="base"/>
      <xsd:enumeration value="sum"/>
      <xsd:enumeration value="repl"/>
      <xsd:enumeration value="mult"/>
      <xsd:enumeration value="none"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLBehaviorAccumulateType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="always"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLBehaviorTransformType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="pt"/>
      <xsd:enumeration value="img"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLBehaviorOverrideType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="normal"/>
      <xsd:enumeration value="childStyle"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLCommonBehaviorData">
    <xsd:sequence>
      <xsd:element name="cTn" type="CT_TLCommonTimeNodeData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tgtEl" type="CT_TLTimeTargetElement" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="attrNameLst" type="CT_TLBehaviorAttributeNameList" minOccurs="0"
        maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="additive" type="ST_TLBehaviorAdditiveType" use="optional"/>
    <xsd:attribute name="accumulate" type="ST_TLBehaviorAccumulateType" use="optional"/>
    <xsd:attribute name="xfrmType" type="ST_TLBehaviorTransformType" use="optional"/>
    <xsd:attribute name="from" type="xsd:string" use="optional"/>
    <xsd:attribute name="to" type="xsd:string" use="optional"/>
    <xsd:attribute name="by" type="xsd:string" use="optional"/>
    <xsd:attribute name="rctx" type="xsd:string" use="optional"/>
    <xsd:attribute name="override" type="ST_TLBehaviorOverrideType" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimVariantBooleanVal">
    <xsd:attribute name="val" type="xsd:boolean" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimVariantIntegerVal">
    <xsd:attribute name="val" type="xsd:int" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimVariantFloatVal">
    <xsd:attribute name="val" type="xsd:float" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimVariantStringVal">
    <xsd:attribute name="val" type="xsd:string" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimVariant">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="boolVal" type="CT_TLAnimVariantBooleanVal"/>
      <xsd:element name="intVal" type="CT_TLAnimVariantIntegerVal"/>
      <xsd:element name="fltVal" type="CT_TLAnimVariantFloatVal"/>
      <xsd:element name="strVal" type="CT_TLAnimVariantStringVal"/>
      <xsd:element name="clrVal" type="a:CT_Color"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLTimeAnimateValueTime">
    <xsd:union memberTypes="a:ST_PositiveFixedPercentage ST_TLTimeIndefinite"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLTimeAnimateValue">
    <xsd:sequence>
      <xsd:element name="val" type="CT_TLAnimVariant" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="tm" type="ST_TLTimeAnimateValueTime" use="optional" default="indefinite"/>
    <xsd:attribute name="fmla" type="xsd:string" use="optional" default=""/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTimeAnimateValueList">
    <xsd:sequence>
      <xsd:element name="tav" type="CT_TLTimeAnimateValue" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLAnimateBehaviorCalcMode">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="discrete"/>
      <xsd:enumeration value="lin"/>
      <xsd:enumeration value="fmla"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLAnimateBehaviorValueType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="str"/>
      <xsd:enumeration value="num"/>
      <xsd:enumeration value="clr"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLAnimateBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tavLst" type="CT_TLTimeAnimateValueList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="by" type="xsd:string" use="optional"/>
    <xsd:attribute name="from" type="xsd:string" use="optional"/>
    <xsd:attribute name="to" type="xsd:string" use="optional"/>
    <xsd:attribute name="calcmode" type="ST_TLAnimateBehaviorCalcMode" use="optional"/>
    <xsd:attribute name="valueType" type="ST_TLAnimateBehaviorValueType" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLByRgbColorTransform">
    <xsd:attribute name="r" type="a:ST_FixedPercentage" use="required"/>
    <xsd:attribute name="g" type="a:ST_FixedPercentage" use="required"/>
    <xsd:attribute name="b" type="a:ST_FixedPercentage" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLByHslColorTransform">
    <xsd:attribute name="h" type="a:ST_Angle" use="required"/>
    <xsd:attribute name="s" type="a:ST_FixedPercentage" use="required"/>
    <xsd:attribute name="l" type="a:ST_FixedPercentage" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLByAnimateColorTransform">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="rgb" type="CT_TLByRgbColorTransform"/>
      <xsd:element name="hsl" type="CT_TLByHslColorTransform"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLAnimateColorSpace">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="rgb"/>
      <xsd:enumeration value="hsl"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLAnimateColorDirection">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="cw"/>
      <xsd:enumeration value="ccw"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLAnimateColorBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="by" type="CT_TLByAnimateColorTransform" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="from" type="a:CT_Color" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="to" type="a:CT_Color" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="clrSpc" type="ST_TLAnimateColorSpace" use="optional"/>
    <xsd:attribute name="dir" type="ST_TLAnimateColorDirection" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLAnimateEffectTransition">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="in"/>
      <xsd:enumeration value="out"/>
      <xsd:enumeration value="none"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLAnimateEffectBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="progress" type="CT_TLAnimVariant" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="transition" type="ST_TLAnimateEffectTransition" default="in" use="optional"/>
    <xsd:attribute name="filter" type="xsd:string" use="optional"/>
    <xsd:attribute name="prLst" type="xsd:string" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLAnimateMotionBehaviorOrigin">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="parent"/>
      <xsd:enumeration value="layout"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_TLAnimateMotionPathEditMode">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="relative"/>
      <xsd:enumeration value="fixed"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLPoint">
    <xsd:attribute name="x" type="a:ST_Percentage" use="required"/>
    <xsd:attribute name="y" type="a:ST_Percentage" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimateMotionBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="by" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="from" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="to" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="rCtr" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="origin" type="ST_TLAnimateMotionBehaviorOrigin" use="optional"/>
    <xsd:attribute name="path" type="xsd:string" use="optional"/>
    <xsd:attribute name="pathEditMode" type="ST_TLAnimateMotionPathEditMode" use="optional"/>
    <xsd:attribute name="rAng" type="a:ST_Angle" use="optional"/>
    <xsd:attribute name="ptsTypes" type="xsd:string" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimateRotationBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="by" type="a:ST_Angle" use="optional"/>
    <xsd:attribute name="from" type="a:ST_Angle" use="optional"/>
    <xsd:attribute name="to" type="a:ST_Angle" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLAnimateScaleBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="by" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="from" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="to" type="CT_TLPoint" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="zoomContents" type="xsd:boolean" use="optional"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLCommandType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="evt"/>
      <xsd:enumeration value="call"/>
      <xsd:enumeration value="verb"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLCommandBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute type="ST_TLCommandType" name="type" use="optional"/>
    <xsd:attribute name="cmd" type="xsd:string" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLSetBehavior">
    <xsd:sequence>
      <xsd:element name="cBhvr" type="CT_TLCommonBehaviorData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="to" type="CT_TLAnimVariant" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_TLCommonMediaNodeData">
    <xsd:sequence>
      <xsd:element name="cTn" type="CT_TLCommonTimeNodeData" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="tgtEl" type="CT_TLTimeTargetElement" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="vol" type="a:ST_PositiveFixedPercentage" default="50%" use="optional"/>
    <xsd:attribute name="mute" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="numSld" type="xsd:unsignedInt" use="optional" default="1"/>
    <xsd:attribute name="showWhenStopped" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLMediaNodeAudio">
    <xsd:sequence>
      <xsd:element name="cMediaNode" type="CT_TLCommonMediaNodeData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="isNarration" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLMediaNodeVideo">
    <xsd:sequence>
      <xsd:element name="cMediaNode" type="CT_TLCommonMediaNodeData" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="fullScrn" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:attributeGroup name="AG_TLBuild">
    <xsd:attribute name="spid" type="a:ST_DrawingElementId" use="required"/>
    <xsd:attribute name="grpId" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="uiExpand" type="xsd:boolean" use="optional" default="false"/>
  </xsd:attributeGroup>
  <xsd:complexType name="CT_TLTemplate">
    <xsd:sequence>
      <xsd:element name="tnLst" type="CT_TimeNodeList" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="lvl" type="xsd:unsignedInt" use="optional" default="0"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLTemplateList">
    <xsd:sequence>
      <xsd:element name="tmpl" type="CT_TLTemplate" minOccurs="0" maxOccurs="9"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLParaBuildType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="allAtOnce"/>
      <xsd:enumeration value="p"/>
      <xsd:enumeration value="cust"/>
      <xsd:enumeration value="whole"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLBuildParagraph">
    <xsd:sequence>
      <xsd:element name="tmplLst" type="CT_TLTemplateList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_TLBuild"/>
    <xsd:attribute name="build" type="ST_TLParaBuildType" use="optional" default="whole"/>
    <xsd:attribute name="bldLvl" type="xsd:unsignedInt" use="optional" default="1"/>
    <xsd:attribute name="animBg" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="autoUpdateAnimBg" type="xsd:boolean" default="true" use="optional"/>
    <xsd:attribute name="rev" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="advAuto" type="ST_TLTime" use="optional" default="indefinite"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLDiagramBuildType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="whole"/>
      <xsd:enumeration value="depthByNode"/>
      <xsd:enumeration value="depthByBranch"/>
      <xsd:enumeration value="breadthByNode"/>
      <xsd:enumeration value="breadthByLvl"/>
      <xsd:enumeration value="cw"/>
      <xsd:enumeration value="cwIn"/>
      <xsd:enumeration value="cwOut"/>
      <xsd:enumeration value="ccw"/>
      <xsd:enumeration value="ccwIn"/>
      <xsd:enumeration value="ccwOut"/>
      <xsd:enumeration value="inByRing"/>
      <xsd:enumeration value="outByRing"/>
      <xsd:enumeration value="up"/>
      <xsd:enumeration value="down"/>
      <xsd:enumeration value="allAtOnce"/>
      <xsd:enumeration value="cust"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLBuildDiagram">
    <xsd:attributeGroup ref="AG_TLBuild"/>
    <xsd:attribute name="bld" type="ST_TLDiagramBuildType" use="optional" default="whole"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_TLOleChartBuildType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="allAtOnce"/>
      <xsd:enumeration value="series"/>
      <xsd:enumeration value="category"/>
      <xsd:enumeration value="seriesEl"/>
      <xsd:enumeration value="categoryEl"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_TLOleBuildChart">
    <xsd:attributeGroup ref="AG_TLBuild"/>
    <xsd:attribute name="bld" type="ST_TLOleChartBuildType" use="optional" default="allAtOnce"/>
    <xsd:attribute name="animBg" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TLGraphicalObjectBuild">
    <xsd:choice minOccurs="1" maxOccurs="1">
      <xsd:element name="bldAsOne" type="CT_Empty"/>
      <xsd:element name="bldSub" type="a:CT_AnimationGraphicalObjectBuildProperties"/>
    </xsd:choice>
    <xsd:attributeGroup ref="AG_TLBuild"/>
  </xsd:complexType>
  <xsd:complexType name="CT_BuildList">
    <xsd:choice minOccurs="1" maxOccurs="unbounded">
      <xsd:element name="bldP" type="CT_TLBuildParagraph"/>
      <xsd:element name="bldDgm" type="CT_TLBuildDiagram"/>
      <xsd:element name="bldOleChart" type="CT_TLOleBuildChart"/>
      <xsd:element name="bldGraphic" type="CT_TLGraphicalObjectBuild"/>
    </xsd:choice>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideTiming">
    <xsd:sequence>
      <xsd:element name="tnLst" type="CT_TimeNodeList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bldLst" type="CT_BuildList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Empty"/>
  <xsd:simpleType name="ST_Name">
    <xsd:restriction base="xsd:string"/>
  </xsd:simpleType>
  <xsd:simpleType name="ST_Direction">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="horz"/>
      <xsd:enumeration value="vert"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_Index">
    <xsd:restriction base="xsd:unsignedInt"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_IndexRange">
    <xsd:attribute name="st" type="ST_Index" use="required"/>
    <xsd:attribute name="end" type="ST_Index" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideRelationshipListEntry">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideRelationshipList">
    <xsd:sequence>
      <xsd:element name="sld" type="CT_SlideRelationshipListEntry" minOccurs="0"
        maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_CustomShowId">
    <xsd:attribute name="id" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:group name="EG_SlideListChoice">
    <xsd:choice>
      <xsd:element name="sldAll" type="CT_Empty"/>
      <xsd:element name="sldRg" type="CT_IndexRange"/>
      <xsd:element name="custShow" type="CT_CustomShowId"/>
    </xsd:choice>
  </xsd:group>
  <xsd:complexType name="CT_CustomerData">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TagsData">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CustomerDataList">
    <xsd:sequence minOccurs="0" maxOccurs="1">
      <xsd:element name="custData" type="CT_CustomerData" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="tags" type="CT_TagsData" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Extension">
    <xsd:sequence>
      <xsd:any processContents="lax" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
    <xsd:attribute name="uri" type="xsd:token" use="required"/>
  </xsd:complexType>
  <xsd:group name="EG_ExtensionList">
    <xsd:sequence>
      <xsd:element name="ext" type="CT_Extension" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:complexType name="CT_ExtensionList">
    <xsd:sequence>
      <xsd:group ref="EG_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_ExtensionListModify">
    <xsd:sequence>
      <xsd:group ref="EG_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="mod" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CommentAuthor">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="name" type="ST_Name" use="required"/>
    <xsd:attribute name="initials" type="ST_Name" use="required"/>
    <xsd:attribute name="lastIdx" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="clrIdx" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CommentAuthorList">
    <xsd:sequence>
      <xsd:element name="cmAuthor" type="CT_CommentAuthor" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="cmAuthorLst" type="CT_CommentAuthorList"/>
  <xsd:complexType name="CT_Comment">
    <xsd:sequence>
      <xsd:element name="pos" type="a:CT_Point2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="text" type="xsd:string" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="authorId" type="xsd:unsignedInt" use="required"/>
    <xsd:attribute name="dt" type="xsd:dateTime" use="optional"/>
    <xsd:attribute name="idx" type="ST_Index" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CommentList">
    <xsd:sequence>
      <xsd:element name="cm" type="CT_Comment" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="cmLst" type="CT_CommentList"/>
  <xsd:attributeGroup name="AG_Ole">
    <xsd:attribute name="spid" type="a:ST_ShapeID" use="optional"/>
    <xsd:attribute name="name" type="xsd:string" use="optional" default=""/>
    <xsd:attribute name="showAsIcon" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute ref="r:id" use="optional"/>
    <xsd:attribute name="imgW" type="a:ST_PositiveCoordinate32" use="optional"/>
    <xsd:attribute name="imgH" type="a:ST_PositiveCoordinate32" use="optional"/>
  </xsd:attributeGroup>
  <xsd:simpleType name="ST_OleObjectFollowColorScheme">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="full"/>
      <xsd:enumeration value="textAndBackground"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_OleObjectEmbed">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="followColorScheme" type="ST_OleObjectFollowColorScheme" use="optional"
      default="none"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OleObjectLink">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="updateAutomatic" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OleObject">
    <xsd:sequence>
      <xsd:choice minOccurs="1" maxOccurs="1">
        <xsd:element name="embed" type="CT_OleObjectEmbed"/>
        <xsd:element name="link" type="CT_OleObjectLink"/>
      </xsd:choice>
      <xsd:element name="pic" type="CT_Picture" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_Ole"/>
    <xsd:attribute name="progId" type="xsd:string" use="optional"/>
  </xsd:complexType>
  <xsd:element name="oleObj" type="CT_OleObject"/>
  <xsd:complexType name="CT_Control">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="pic" type="CT_Picture" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_Ole"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ControlList">
    <xsd:sequence>
      <xsd:element name="control" type="CT_Control" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_SlideId">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="256"/>
      <xsd:maxExclusive value="2147483648"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideIdListEntry">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="ST_SlideId" use="required"/>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideIdList">
    <xsd:sequence>
      <xsd:element name="sldId" type="CT_SlideIdListEntry" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_SlideMasterId">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="2147483648"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideMasterIdListEntry">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="ST_SlideMasterId" use="optional"/>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideMasterIdList">
    <xsd:sequence>
      <xsd:element name="sldMasterId" type="CT_SlideMasterIdListEntry" minOccurs="0"
        maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_NotesMasterIdListEntry">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_NotesMasterIdList">
    <xsd:sequence>
      <xsd:element name="notesMasterId" type="CT_NotesMasterIdListEntry" minOccurs="0" maxOccurs="1"
      />
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_HandoutMasterIdListEntry">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_HandoutMasterIdList">
    <xsd:sequence>
      <xsd:element name="handoutMasterId" type="CT_HandoutMasterIdListEntry" minOccurs="0"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_EmbeddedFontDataId">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_EmbeddedFontListEntry">
    <xsd:sequence>
      <xsd:element name="font" type="a:CT_TextFont" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="regular" type="CT_EmbeddedFontDataId" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bold" type="CT_EmbeddedFontDataId" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="italic" type="CT_EmbeddedFontDataId" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="boldItalic" type="CT_EmbeddedFontDataId" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_EmbeddedFontList">
    <xsd:sequence>
      <xsd:element name="embeddedFont" type="CT_EmbeddedFontListEntry" minOccurs="0"
        maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SmartTags">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CustomShow">
    <xsd:sequence>
      <xsd:element name="sldLst" type="CT_SlideRelationshipList" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="name" type="ST_Name" use="required"/>
    <xsd:attribute name="id" type="xsd:unsignedInt" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CustomShowList">
    <xsd:sequence>
      <xsd:element name="custShow" type="CT_CustomShow" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_PhotoAlbumLayout">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="fitToSlide"/>
      <xsd:enumeration value="1pic"/>
      <xsd:enumeration value="2pic"/>
      <xsd:enumeration value="4pic"/>
      <xsd:enumeration value="1picTitle"/>
      <xsd:enumeration value="2picTitle"/>
      <xsd:enumeration value="4picTitle"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_PhotoAlbumFrameShape">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="frameStyle1"/>
      <xsd:enumeration value="frameStyle2"/>
      <xsd:enumeration value="frameStyle3"/>
      <xsd:enumeration value="frameStyle4"/>
      <xsd:enumeration value="frameStyle5"/>
      <xsd:enumeration value="frameStyle6"/>
      <xsd:enumeration value="frameStyle7"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PhotoAlbum">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="bw" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="showCaptions" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="layout" type="ST_PhotoAlbumLayout" use="optional" default="fitToSlide"/>
    <xsd:attribute name="frame" type="ST_PhotoAlbumFrameShape" use="optional" default="frameStyle1"
    />
  </xsd:complexType>
  <xsd:simpleType name="ST_SlideSizeCoordinate">
    <xsd:restriction base="a:ST_PositiveCoordinate32">
      <xsd:minInclusive value="914400"/>
      <xsd:maxInclusive value="51206400"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_SlideSizeType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="screen4x3"/>
      <xsd:enumeration value="letter"/>
      <xsd:enumeration value="A4"/>
      <xsd:enumeration value="35mm"/>
      <xsd:enumeration value="overhead"/>
      <xsd:enumeration value="banner"/>
      <xsd:enumeration value="custom"/>
      <xsd:enumeration value="ledger"/>
      <xsd:enumeration value="A3"/>
      <xsd:enumeration value="B4ISO"/>
      <xsd:enumeration value="B5ISO"/>
      <xsd:enumeration value="B4JIS"/>
      <xsd:enumeration value="B5JIS"/>
      <xsd:enumeration value="hagakiCard"/>
      <xsd:enumeration value="screen16x9"/>
      <xsd:enumeration value="screen16x10"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideSize">
    <xsd:attribute name="cx" type="ST_SlideSizeCoordinate" use="required"/>
    <xsd:attribute name="cy" type="ST_SlideSizeCoordinate" use="required"/>
    <xsd:attribute name="type" type="ST_SlideSizeType" use="optional" default="custom"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Kinsoku">
    <xsd:attribute name="lang" type="xsd:string" use="optional"/>
    <xsd:attribute name="invalStChars" type="xsd:string" use="required"/>
    <xsd:attribute name="invalEndChars" type="xsd:string" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_BookmarkIdSeed">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="1"/>
      <xsd:maxExclusive value="2147483648"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_ModifyVerifier">
    <xsd:attribute name="algorithmName" type="xsd:string" use="optional"/>
    <xsd:attribute name="hashValue" type="xsd:base64Binary" use="optional"/>
    <xsd:attribute name="saltValue" type="xsd:base64Binary" use="optional"/>
    <xsd:attribute name="spinValue" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="cryptProviderType" type="s:ST_CryptProv" use="optional"/>
    <xsd:attribute name="cryptAlgorithmClass" type="s:ST_AlgClass" use="optional"/>
    <xsd:attribute name="cryptAlgorithmType" type="s:ST_AlgType" use="optional"/>
    <xsd:attribute name="cryptAlgorithmSid" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="spinCount" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="saltData" type="xsd:base64Binary" use="optional"/>
    <xsd:attribute name="hashData" type="xsd:base64Binary" use="optional"/>
    <xsd:attribute name="cryptProvider" type="xsd:string" use="optional"/>
    <xsd:attribute name="algIdExt" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="algIdExtSource" type="xsd:string" use="optional"/>
    <xsd:attribute name="cryptProviderTypeExt" type="xsd:unsignedInt" use="optional"/>
    <xsd:attribute name="cryptProviderTypeExtSource" type="xsd:string" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Presentation">
    <xsd:sequence>
      <xsd:element name="sldMasterIdLst" type="CT_SlideMasterIdList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="notesMasterIdLst" type="CT_NotesMasterIdList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="handoutMasterIdLst" type="CT_HandoutMasterIdList" minOccurs="0"
        maxOccurs="1"/>
      <xsd:element name="sldIdLst" type="CT_SlideIdList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="sldSz" type="CT_SlideSize" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="notesSz" type="a:CT_PositiveSize2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="smartTags" type="CT_SmartTags" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="embeddedFontLst" type="CT_EmbeddedFontList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="custShowLst" type="CT_CustomShowList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="photoAlbum" type="CT_PhotoAlbum" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="custDataLst" type="CT_CustomerDataList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="kinsoku" type="CT_Kinsoku" minOccurs="0"/>
      <xsd:element name="defaultTextStyle" type="a:CT_TextListStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="modifyVerifier" type="CT_ModifyVerifier" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="serverZoom" type="a:ST_Percentage" use="optional" default="50%"/>
    <xsd:attribute name="firstSlideNum" type="xsd:int" use="optional" default="1"/>
    <xsd:attribute name="showSpecialPlsOnTitleSld" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="rtl" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="removePersonalInfoOnSave" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="compatMode" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="strictFirstAndLastChars" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="embedTrueTypeFonts" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="saveSubsetFonts" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="autoCompressPictures" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="bookmarkIdSeed" type="ST_BookmarkIdSeed" use="optional" default="1"/>
    <xsd:attribute name="conformance" type="s:ST_ConformanceClass"/>
  </xsd:complexType>
  <xsd:element name="presentation" type="CT_Presentation"/>
  <xsd:complexType name="CT_HtmlPublishProperties">
    <xsd:sequence>
      <xsd:group ref="EG_SlideListChoice" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="showSpeakerNotes" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="target" type="xsd:string" use="optional"/>
    <xsd:attribute name="title" type="xsd:string" use="optional" default=""/>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_WebColorType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="none"/>
      <xsd:enumeration value="browser"/>
      <xsd:enumeration value="presentationText"/>
      <xsd:enumeration value="presentationAccent"/>
      <xsd:enumeration value="whiteTextOnBlack"/>
      <xsd:enumeration value="blackTextOnWhite"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_WebScreenSize">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="544x376"/>
      <xsd:enumeration value="640x480"/>
      <xsd:enumeration value="720x512"/>
      <xsd:enumeration value="800x600"/>
      <xsd:enumeration value="1024x768"/>
      <xsd:enumeration value="1152x882"/>
      <xsd:enumeration value="1152x900"/>
      <xsd:enumeration value="1280x1024"/>
      <xsd:enumeration value="1600x1200"/>
      <xsd:enumeration value="1800x1400"/>
      <xsd:enumeration value="1920x1200"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_WebEncoding">
    <xsd:restriction base="xsd:string"/>
  </xsd:simpleType>
  <xsd:complexType name="CT_WebProperties">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="showAnimation" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="resizeGraphics" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="allowPng" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="relyOnVml" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="organizeInFolders" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="useLongFilenames" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="imgSz" type="ST_WebScreenSize" use="optional" default="800x600"/>
    <xsd:attribute name="encoding" type="ST_WebEncoding" use="optional" default=""/>
    <xsd:attribute name="clr" type="ST_WebColorType" use="optional" default="whiteTextOnBlack"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_PrintWhat">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="slides"/>
      <xsd:enumeration value="handouts1"/>
      <xsd:enumeration value="handouts2"/>
      <xsd:enumeration value="handouts3"/>
      <xsd:enumeration value="handouts4"/>
      <xsd:enumeration value="handouts6"/>
      <xsd:enumeration value="handouts9"/>
      <xsd:enumeration value="notes"/>
      <xsd:enumeration value="outline"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_PrintColorMode">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="bw"/>
      <xsd:enumeration value="gray"/>
      <xsd:enumeration value="clr"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_PrintProperties">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="prnWhat" type="ST_PrintWhat" use="optional" default="slides"/>
    <xsd:attribute name="clrMode" type="ST_PrintColorMode" use="optional" default="clr"/>
    <xsd:attribute name="hiddenSlides" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="scaleToFitPaper" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="frameSlides" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ShowInfoBrowse">
    <xsd:attribute name="showScrollbar" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ShowInfoKiosk">
    <xsd:attribute name="restart" type="xsd:unsignedInt" use="optional" default="300000"/>
  </xsd:complexType>
  <xsd:group name="EG_ShowType">
    <xsd:choice>
      <xsd:element name="present" type="CT_Empty"/>
      <xsd:element name="browse" type="CT_ShowInfoBrowse"/>
      <xsd:element name="kiosk" type="CT_ShowInfoKiosk"/>
    </xsd:choice>
  </xsd:group>
  <xsd:complexType name="CT_ShowProperties">
    <xsd:sequence minOccurs="0" maxOccurs="1">
      <xsd:group ref="EG_ShowType" minOccurs="0" maxOccurs="1"/>
      <xsd:group ref="EG_SlideListChoice" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="penClr" type="a:CT_Color" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="loop" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="showNarration" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="showAnimation" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="useTimings" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_PresentationProperties">
    <xsd:sequence>
      <xsd:element name="htmlPubPr" type="CT_HtmlPublishProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="webPr" type="CT_WebProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="prnPr" type="CT_PrintProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="showPr" type="CT_ShowProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="clrMru" type="a:CT_ColorMRU" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="presentationPr" type="CT_PresentationProperties"/>
  <xsd:complexType name="CT_HeaderFooter">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="sldNum" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="hdr" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="ftr" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="dt" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:simpleType name="ST_PlaceholderType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="title"/>
      <xsd:enumeration value="body"/>
      <xsd:enumeration value="ctrTitle"/>
      <xsd:enumeration value="subTitle"/>
      <xsd:enumeration value="dt"/>
      <xsd:enumeration value="sldNum"/>
      <xsd:enumeration value="ftr"/>
      <xsd:enumeration value="hdr"/>
      <xsd:enumeration value="obj"/>
      <xsd:enumeration value="chart"/>
      <xsd:enumeration value="tbl"/>
      <xsd:enumeration value="clipArt"/>
      <xsd:enumeration value="dgm"/>
      <xsd:enumeration value="media"/>
      <xsd:enumeration value="sldImg"/>
      <xsd:enumeration value="pic"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_PlaceholderSize">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="full"/>
      <xsd:enumeration value="half"/>
      <xsd:enumeration value="quarter"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_Placeholder">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="type" type="ST_PlaceholderType" use="optional" default="obj"/>
    <xsd:attribute name="orient" type="ST_Direction" use="optional" default="horz"/>
    <xsd:attribute name="sz" type="ST_PlaceholderSize" use="optional" default="full"/>
    <xsd:attribute name="idx" type="xsd:unsignedInt" use="optional" default="0"/>
    <xsd:attribute name="hasCustomPrompt" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ApplicationNonVisualDrawingProps">
    <xsd:sequence>
      <xsd:element name="ph" type="CT_Placeholder" minOccurs="0" maxOccurs="1"/>
      <xsd:group ref="a:EG_Media" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="custDataLst" type="CT_CustomerDataList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="isPhoto" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="userDrawn" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ShapeNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvSpPr" type="a:CT_NonVisualDrawingShapeProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="nvPr" type="CT_ApplicationNonVisualDrawingProps" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Shape">
    <xsd:sequence>
      <xsd:element name="nvSpPr" type="CT_ShapeNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txBody" type="a:CT_TextBody" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="useBgFill" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_ConnectorNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvCxnSpPr" type="a:CT_NonVisualConnectorProperties" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="nvPr" type="CT_ApplicationNonVisualDrawingProps" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Connector">
    <xsd:sequence>
      <xsd:element name="nvCxnSpPr" type="CT_ConnectorNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_PictureNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvPicPr" type="a:CT_NonVisualPictureProperties" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="nvPr" type="CT_ApplicationNonVisualDrawingProps" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Picture">
    <xsd:sequence>
      <xsd:element name="nvPicPr" type="CT_PictureNonVisual" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="blipFill" type="a:CT_BlipFillProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="spPr" type="a:CT_ShapeProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="style" type="a:CT_ShapeStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicalObjectFrameNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGraphicFramePr" type="a:CT_NonVisualGraphicFrameProperties"
        minOccurs="1" maxOccurs="1"/>
      <xsd:element name="nvPr" type="CT_ApplicationNonVisualDrawingProps" minOccurs="1"
        maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_GraphicalObjectFrame">
    <xsd:sequence>
      <xsd:element name="nvGraphicFramePr" type="CT_GraphicalObjectFrameNonVisual" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="xfrm" type="a:CT_Transform2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element ref="a:graphic" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="bwMode" type="a:ST_BlackWhiteMode" use="optional"/>
  </xsd:complexType>
  <xsd:complexType name="CT_GroupShapeNonVisual">
    <xsd:sequence>
      <xsd:element name="cNvPr" type="a:CT_NonVisualDrawingProps" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="cNvGrpSpPr" type="a:CT_NonVisualGroupDrawingShapeProps" minOccurs="1"
        maxOccurs="1"/>
      <xsd:element name="nvPr" type="CT_ApplicationNonVisualDrawingProps" minOccurs="1"
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
        <xsd:element name="contentPart" type="CT_Rel"/>
      </xsd:choice>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_Rel">
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:group name="EG_TopLevelSlide">
    <xsd:sequence>
      <xsd:element name="clrMap" type="a:CT_ColorMapping" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:group name="EG_ChildSlide">
    <xsd:sequence>
      <xsd:element name="clrMapOvr" type="a:CT_ColorMappingOverride" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:group>
  <xsd:attributeGroup name="AG_ChildSlide">
    <xsd:attribute name="showMasterSp" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="showMasterPhAnim" type="xsd:boolean" use="optional" default="true"/>
  </xsd:attributeGroup>
  <xsd:complexType name="CT_BackgroundProperties">
    <xsd:sequence>
      <xsd:group ref="a:EG_FillProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="a:EG_EffectProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="shadeToTitle" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:group name="EG_Background">
    <xsd:choice>
      <xsd:element name="bgPr" type="CT_BackgroundProperties"/>
      <xsd:element name="bgRef" type="a:CT_StyleMatrixReference"/>
    </xsd:choice>
  </xsd:group>
  <xsd:complexType name="CT_Background">
    <xsd:sequence>
      <xsd:group ref="EG_Background"/>
    </xsd:sequence>
    <xsd:attribute name="bwMode" type="a:ST_BlackWhiteMode" use="optional" default="white"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CommonSlideData">
    <xsd:sequence>
      <xsd:element name="bg" type="CT_Background" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="spTree" type="CT_GroupShape" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="custDataLst" type="CT_CustomerDataList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="controls" type="CT_ControlList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="name" type="xsd:string" use="optional" default=""/>
  </xsd:complexType>
  <xsd:complexType name="CT_Slide">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_ChildSlide" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="transition" type="CT_SlideTransition" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="timing" type="CT_SlideTiming" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_ChildSlide"/>
    <xsd:attribute name="show" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:element name="sld" type="CT_Slide"/>
  <xsd:simpleType name="ST_SlideLayoutType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="title"/>
      <xsd:enumeration value="tx"/>
      <xsd:enumeration value="twoColTx"/>
      <xsd:enumeration value="tbl"/>
      <xsd:enumeration value="txAndChart"/>
      <xsd:enumeration value="chartAndTx"/>
      <xsd:enumeration value="dgm"/>
      <xsd:enumeration value="chart"/>
      <xsd:enumeration value="txAndClipArt"/>
      <xsd:enumeration value="clipArtAndTx"/>
      <xsd:enumeration value="titleOnly"/>
      <xsd:enumeration value="blank"/>
      <xsd:enumeration value="txAndObj"/>
      <xsd:enumeration value="objAndTx"/>
      <xsd:enumeration value="objOnly"/>
      <xsd:enumeration value="obj"/>
      <xsd:enumeration value="txAndMedia"/>
      <xsd:enumeration value="mediaAndTx"/>
      <xsd:enumeration value="objOverTx"/>
      <xsd:enumeration value="txOverObj"/>
      <xsd:enumeration value="txAndTwoObj"/>
      <xsd:enumeration value="twoObjAndTx"/>
      <xsd:enumeration value="twoObjOverTx"/>
      <xsd:enumeration value="fourObj"/>
      <xsd:enumeration value="vertTx"/>
      <xsd:enumeration value="clipArtAndVertTx"/>
      <xsd:enumeration value="vertTitleAndTx"/>
      <xsd:enumeration value="vertTitleAndTxOverChart"/>
      <xsd:enumeration value="twoObj"/>
      <xsd:enumeration value="objAndTwoObj"/>
      <xsd:enumeration value="twoObjAndObj"/>
      <xsd:enumeration value="cust"/>
      <xsd:enumeration value="secHead"/>
      <xsd:enumeration value="twoTxTwoObj"/>
      <xsd:enumeration value="objTx"/>
      <xsd:enumeration value="picTx"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideLayout">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_ChildSlide" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="transition" type="CT_SlideTransition" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="timing" type="CT_SlideTiming" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="hf" type="CT_HeaderFooter" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_ChildSlide"/>
    <xsd:attribute name="matchingName" type="xsd:string" use="optional" default=""/>
    <xsd:attribute name="type" type="ST_SlideLayoutType" use="optional" default="cust"/>
    <xsd:attribute name="preserve" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="userDrawn" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:element name="sldLayout" type="CT_SlideLayout"/>
  <xsd:complexType name="CT_SlideMasterTextStyles">
    <xsd:sequence>
      <xsd:element name="titleStyle" type="a:CT_TextListStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="bodyStyle" type="a:CT_TextListStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="otherStyle" type="a:CT_TextListStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:simpleType name="ST_SlideLayoutId">
    <xsd:restriction base="xsd:unsignedInt">
      <xsd:minInclusive value="2147483648"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_SlideLayoutIdListEntry">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="id" type="ST_SlideLayoutId" use="optional"/>
    <xsd:attribute ref="r:id" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideLayoutIdList">
    <xsd:sequence>
      <xsd:element name="sldLayoutId" type="CT_SlideLayoutIdListEntry" minOccurs="0"
        maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideMaster">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_TopLevelSlide" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="sldLayoutIdLst" type="CT_SlideLayoutIdList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="transition" type="CT_SlideTransition" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="timing" type="CT_SlideTiming" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="hf" type="CT_HeaderFooter" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="txStyles" type="CT_SlideMasterTextStyles" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="preserve" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:element name="sldMaster" type="CT_SlideMaster"/>
  <xsd:complexType name="CT_HandoutMaster">
    <xsd:sequence>
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_TopLevelSlide" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hf" type="CT_HeaderFooter" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="handoutMaster" type="CT_HandoutMaster"/>
  <xsd:complexType name="CT_NotesMaster">
    <xsd:sequence>
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_TopLevelSlide" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="hf" type="CT_HeaderFooter" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="notesStyle" type="a:CT_TextListStyle" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="notesMaster" type="CT_NotesMaster"/>
  <xsd:complexType name="CT_NotesSlide">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cSld" type="CT_CommonSlideData" minOccurs="1" maxOccurs="1"/>
      <xsd:group ref="EG_ChildSlide" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionListModify" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attributeGroup ref="AG_ChildSlide"/>
  </xsd:complexType>
  <xsd:element name="notes" type="CT_NotesSlide"/>
  <xsd:complexType name="CT_SlideSyncProperties">
    <xsd:sequence>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="serverSldId" type="xsd:string" use="required"/>
    <xsd:attribute name="serverSldModifiedTime" type="xsd:dateTime" use="required"/>
    <xsd:attribute name="clientInsertedTime" type="xsd:dateTime" use="required"/>
  </xsd:complexType>
  <xsd:element name="sldSyncPr" type="CT_SlideSyncProperties"/>
  <xsd:complexType name="CT_StringTag">
    <xsd:attribute name="name" type="xsd:string" use="required"/>
    <xsd:attribute name="val" type="xsd:string" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_TagList">
    <xsd:sequence>
      <xsd:element name="tag" type="CT_StringTag" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="tagLst" type="CT_TagList"/>
  <xsd:simpleType name="ST_SplitterBarState">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="minimized"/>
      <xsd:enumeration value="restored"/>
      <xsd:enumeration value="maximized"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:simpleType name="ST_ViewType">
    <xsd:restriction base="xsd:token">
      <xsd:enumeration value="sldView"/>
      <xsd:enumeration value="sldMasterView"/>
      <xsd:enumeration value="notesView"/>
      <xsd:enumeration value="handoutView"/>
      <xsd:enumeration value="notesMasterView"/>
      <xsd:enumeration value="outlineView"/>
      <xsd:enumeration value="sldSorterView"/>
      <xsd:enumeration value="sldThumbnailView"/>
    </xsd:restriction>
  </xsd:simpleType>
  <xsd:complexType name="CT_NormalViewPortion">
    <xsd:attribute name="sz" type="a:ST_PositiveFixedPercentage" use="required"/>
    <xsd:attribute name="autoAdjust" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_NormalViewProperties">
    <xsd:sequence>
      <xsd:element name="restoredLeft" type="CT_NormalViewPortion" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="restoredTop" type="CT_NormalViewPortion" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="showOutlineIcons" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="snapVertSplitter" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="vertBarState" type="ST_SplitterBarState" use="optional" default="restored"/>
    <xsd:attribute name="horzBarState" type="ST_SplitterBarState" use="optional" default="restored"/>
    <xsd:attribute name="preferSingleView" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_CommonViewProperties">
    <xsd:sequence>
      <xsd:element name="scale" type="a:CT_Scale2D" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="origin" type="a:CT_Point2D" minOccurs="1" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="varScale" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_NotesTextViewProperties">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cViewPr" type="CT_CommonViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_OutlineViewSlideEntry">
    <xsd:attribute ref="r:id" use="required"/>
    <xsd:attribute name="collapse" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_OutlineViewSlideList">
    <xsd:sequence>
      <xsd:element name="sld" type="CT_OutlineViewSlideEntry" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_OutlineViewProperties">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cViewPr" type="CT_CommonViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="sldLst" type="CT_OutlineViewSlideList" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideSorterViewProperties">
    <xsd:sequence minOccurs="1" maxOccurs="1">
      <xsd:element name="cViewPr" type="CT_CommonViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="showFormatting" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:complexType name="CT_Guide">
    <xsd:attribute name="orient" type="ST_Direction" use="optional" default="vert"/>
    <xsd:attribute name="pos" type="a:ST_Coordinate32" use="optional" default="0"/>
  </xsd:complexType>
  <xsd:complexType name="CT_GuideList">
    <xsd:sequence minOccurs="0" maxOccurs="1">
      <xsd:element name="guide" type="CT_Guide" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_CommonSlideViewProperties">
    <xsd:sequence>
      <xsd:element name="cViewPr" type="CT_CommonViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="guideLst" type="CT_GuideList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="snapToGrid" type="xsd:boolean" use="optional" default="true"/>
    <xsd:attribute name="snapToObjects" type="xsd:boolean" use="optional" default="false"/>
    <xsd:attribute name="showGuides" type="xsd:boolean" use="optional" default="false"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SlideViewProperties">
    <xsd:sequence>
      <xsd:element name="cSldViewPr" type="CT_CommonSlideViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_NotesViewProperties">
    <xsd:sequence>
      <xsd:element name="cSldViewPr" type="CT_CommonSlideViewProperties" minOccurs="1" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_ViewProperties">
    <xsd:sequence minOccurs="0" maxOccurs="1">
      <xsd:element name="normalViewPr" type="CT_NormalViewProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="slideViewPr" type="CT_SlideViewProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="outlineViewPr" type="CT_OutlineViewProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="notesTextViewPr" type="CT_NotesTextViewProperties" minOccurs="0"
        maxOccurs="1"/>
      <xsd:element name="sorterViewPr" type="CT_SlideSorterViewProperties" minOccurs="0"
        maxOccurs="1"/>
      <xsd:element name="notesViewPr" type="CT_NotesViewProperties" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="gridSpacing" type="a:CT_PositiveSize2D" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="extLst" type="CT_ExtensionList" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
    <xsd:attribute name="lastView" type="ST_ViewType" use="optional" default="sldView"/>
    <xsd:attribute name="showComments" type="xsd:boolean" use="optional" default="true"/>
  </xsd:complexType>
  <xsd:element name="viewPr" type="CT_ViewProperties"/>
</xsd:schema>
```
