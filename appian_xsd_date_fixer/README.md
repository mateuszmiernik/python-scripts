# XSD DateTime to Date Converter

A Python script that fixes type mismatches in Appian Custom Data Types (CDT) by converting XSD `dateTime` types to `date` types for database columns defined with `DATE` columnDefinition.

## 🎯 Purpose

When working with Appian CDTs, you may encounter situations where:
- Database columns are defined as `DATE` type
- But XSD schema shows them as `xsd:dateTime` 
- This creates type mismatches between database and Appian data types

**Example Problem:**
```xml
<xsd:element name="valueDateAcctDebitDate" nillable="true" type="xsd:dateTime">
    <xsd:annotation>
        <xsd:appinfo source="appian.jpa">@Column(name="VALUEDATEACCTDEBITDATE", columnDefinition="DATE")</xsd:appinfo>
    </xsd:annotation>
</xsd:element>