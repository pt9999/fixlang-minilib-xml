# Minilib.Encoding.Xml.XmlParser

Defined in minilib-xml@0.5.1

Simple XML 1.1 Parser.

Implemented from specification of XML 1.1:
- [Extensible Markup Language (XML) 1.1 (Second Edition)](https://www.w3.org/TR/2006/REC-xml11-20060816/)

Known Problems:
- Currently only UTF-8 encoding is supported.
- Currently Document Type Definition (DTD) is not supported.

## Values

### namespace Minilib.Encoding.Xml.XmlParser

#### _DoubleQuote

Type: `Std::U8`

#### _SingleQuote

Type: `Std::U8`

#### _negative_lookahead

Type: `Std::String -> Minilib.Text.SimpleParser::Parser ()`

Checks whether it does not match `str` at current position.
Raises `_NotMatch` if it matches.

#### _parse_att_value

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[10]   	AttValue	   ::=   	'"' ([^<&"] | Reference)* '"'
                              |  "'" ([^<&'] | Reference)* "'"

#### _parse_attribute

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlAttribute`

[41]   	Attribute	   ::=   	Name Eq AttValue

#### _parse_cdsect

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

[18]   	CDSect	   ::=   	CDStart CData CDEnd
[19]   	CDStart	   ::=   	'<![CDATA['
[20]   	CData	   ::=   	(Char* - (Char* ']]>' Char*))
[21]   	CDEnd	   ::=   	']]>'

#### _parse_char_data

Type: `Minilib.Text.SimpleParser::Parser Std::String`

Character Data
[14]   	CharData	   ::=   	[^<&]* - ([^<&]* ']]>' [^<&]*)

#### _parse_char_ref

Type: `Minilib.Text.SimpleParser::Parser ()`

Character Reference
[66]   	CharRef	   ::=   	'&#' [0-9]+ ';'
                             | '&#x' [0-9a-fA-F]+ ';'

#### _parse_comment

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

[15]   	Comment	   ::=   	'<!--' ((Char - '-') | ('-' (Char - '-')))* '-->'

#### _parse_content

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlElement`

Content of Elements
[43]   	content	   ::=   	CharData? ((element | Reference | CDSect | PI | Comment) CharData?)*

#### _parse_document

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlDocument`

[1]   	document	   ::=   	( prolog element Misc* ) - ( Char* RestrictedChar Char* )

#### _parse_element

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlElement`

[39]   	element	   ::=   	EmptyElemTag
                             | STag content ETag

#### _parse_empty_elem_tag_or_stag

Type: `Minilib.Text.SimpleParser::Parser (Std::Bool, Minilib.Encoding.Xml::XmlElement)`

[44]   	EmptyElemTag	   ::=   	'<' Name (S Attribute)* S? '/>'
[40]   	STag	   ::=   	'<' Name (S Attribute)* S? '>'

#### _parse_enc_name

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[81]   	EncName	   ::=   	[A-Za-z] ([A-Za-z0-9._] | '-')*

#### _parse_encoding_decl

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[80]   	EncodingDecl	   ::=   	S 'encoding' Eq ('"' EncName '"' | "'" EncName "'" )

#### _parse_entity_ref

Type: `Minilib.Text.SimpleParser::Parser ()`

[68]   	EntityRef	   ::=   	'&' Name ';'

#### _parse_eq

Type: `Minilib.Text.SimpleParser::Parser ()`

[25]   	Eq	   ::=   	S? '=' S?

#### _parse_etag

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlElement`

[42]   	ETag	   ::=   	'</' Name S? '>'

#### _parse_misc

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

[27]   	Misc	   ::=   	Comment | PI | S

#### _parse_name

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[5]   	Name	   ::=   	NameStartChar (NameChar)*

#### _parse_name_char

Type: `Minilib.Text.SimpleParser::Parser Minilib.Text.SimpleParser::Char`

[4a]   	NameChar	   ::=   	NameStartChar | "-" | "." | [0-9] |
                                  #xB7 | [#x0300-#x036F] | [#x203F-#x2040]

#### _parse_name_start_char

Type: `Minilib.Text.SimpleParser::Parser Minilib.Text.SimpleParser::Char`

[4]   	NameStartChar	   ::=   	":" | [A-Z] | "_" | [a-z] | [#xC0-#xD6] |
             [#xD8-#xF6] | [#xF8-#x2FF] | [#x370-#x37D] | [#x37F-#x1FFF] |
             [#x200C-#x200D] | [#x2070-#x218F] | [#x2C00-#x2FEF] | [#x3001-#xD7FF] |
             [#xF900-#xFDCF] | [#xFDF0-#xFFFD] | [#x10000-#xEFFFF]

#### _parse_pi

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

[16]   	PI	   ::=   	'<?' PITarget (S (Char* - (Char* '?>' Char*)))? '?>'
[17]   	PITarget	   ::=   	Name - (('X' | 'x') ('M' | 'm') ('L' | 'l'))

#### _parse_prolog

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlDocument`

[22]   	prolog	   ::=   	XMLDecl Misc* (doctypedecl Misc*)?

#### _parse_reference

Type: `Minilib.Text.SimpleParser::Parser ()`

Entity Reference
[67]   	Reference	   ::=   	EntityRef | CharRef

#### _parse_reference_as_text_node

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

#### _parse_s

Type: `Minilib.Text.SimpleParser::Parser Std::String`

White Space
[3]   	S	   ::=   	(#x20 | #x9 | #xD | #xA)+

#### _parse_s_as_text_node

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlNode`

#### _parse_sd_decl

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[32]   	SDDecl	   ::=   	S 'standalone' Eq (("'" ('yes' | 'no') "'") | ('"' ('yes' | 'no') '"'))

#### _parse_version_info

Type: `Minilib.Text.SimpleParser::Parser Std::String`

[24]   	VersionInfo	   ::=   	S 'version' Eq ("'" VersionNum "'" | '"' VersionNum '"')

#### _parse_xml_declaration

Type: `Minilib.Text.SimpleParser::Parser Minilib.Encoding.Xml::XmlDeclaration`

[23]   	XMLDecl	   ::=   	'<?xml' VersionInfo EncodingDecl? SDDecl? S? '?>'

#### _whitespace

Type: `Minilib.Text.SimpleParser::Parser Minilib.Text.SimpleParser::Char`

#### parse_document_from_string

Type: `Std::String -> Std::Result Std::ErrMsg Minilib.Encoding.Xml::XmlDocument`

Reads an XML document from a string.

#### parse_element_from_string

Type: `Std::String -> Std::Result Std::ErrMsg Minilib.Encoding.Xml::XmlElement`

Reads an XML element from a string.

## Types and aliases

## Traits and aliases

## Trait implementations