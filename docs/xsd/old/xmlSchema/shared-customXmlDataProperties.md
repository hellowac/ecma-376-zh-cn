# shared-customXmlDataProperties.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/officeDocument/2006/customXml"
  xmlns:s="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
  targetNamespace="http://schemas.openxmlformats.org/officeDocument/2006/customXml"
  elementFormDefault="qualified" attributeFormDefault="qualified" blockDefault="#all">
  <xsd:import namespace="http://schemas.openxmlformats.org/officeDocument/2006/sharedTypes"
    schemaLocation="shared-commonSimpleTypes.xsd"/>
  <xsd:complexType name="CT_DatastoreSchemaRef">
    <xsd:attribute name="uri" type="xsd:string" use="required"/>
  </xsd:complexType>
  <xsd:complexType name="CT_DatastoreSchemaRefs">
    <xsd:sequence>
      <xsd:element name="schemaRef" type="CT_DatastoreSchemaRef" minOccurs="0" maxOccurs="unbounded"
      />
    </xsd:sequence>
  </xsd:complexType>
  <xsd:complexType name="CT_DatastoreItem">
    <xsd:sequence>
      <xsd:element name="schemaRefs" type="CT_DatastoreSchemaRefs" minOccurs="0"/>
    </xsd:sequence>
    <xsd:attribute name="itemID" type="s:ST_Guid" use="required"/>
  </xsd:complexType>
  <xsd:element name="datastoreItem" type="CT_DatastoreItem"/>
</xsd:schema>
```
