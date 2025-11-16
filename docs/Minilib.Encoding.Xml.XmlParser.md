# Minilib.Encoding.Xml.XmlParser

Defined in minilib-xml@0.5.2

Simple XML 1.1 Parser.

Implemented from specification of XML 1.1:
- [Extensible Markup Language (XML) 1.1 (Second Edition)](https://www.w3.org/TR/2006/REC-xml11-20060816/)

Known Problems:
- Currently only UTF-8 encoding is supported.
- Currently Document Type Definition (DTD) is not supported.

## Values

### namespace Minilib.Encoding.Xml.XmlParser

#### parse_document_from_string

Type: `Std::String -> Std::Result Std::ErrMsg Minilib.Encoding.Xml::XmlDocument`

Reads an XML document from a string.

#### parse_element_from_string

Type: `Std::String -> Std::Result Std::ErrMsg Minilib.Encoding.Xml::XmlElement`

Reads an XML element from a string.

## Types and aliases

## Traits and aliases

## Trait implementations