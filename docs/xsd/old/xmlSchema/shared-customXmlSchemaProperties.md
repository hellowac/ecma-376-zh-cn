# shared-customXmlSchemaProperties.xsd

```xml
<?xml version="1.0" encoding="utf-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.openxmlformats.org/schemaLibrary/2006/main"
  targetNamespace="http://schemas.openxmlformats.org/schemaLibrary/2006/main"
  attributeFormDefault="qualified" elementFormDefault="qualified">
  <xsd:complexType name="CT_Schema">
    <xsd:attribute name="uri" type="xsd:string" default=""/>
    <xsd:attribute name="manifestLocation" type="xsd:string"/>
    <xsd:attribute name="schemaLocation" type="xsd:string"/>
    <xsd:attribute name="schemaLanguage" type="xsd:token"/>
  </xsd:complexType>
  <xsd:complexType name="CT_SchemaLibrary">
    <xsd:sequence>
      <xsd:element name="schema" type="CT_Schema" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>
  <xsd:element name="schemaLibrary" type="CT_SchemaLibrary"/>
</xsd:schema>
```