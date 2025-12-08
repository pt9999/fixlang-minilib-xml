# Minilib.Encoding.Xml

Defined in minilib-xml@0.5.3

Simple XML Model.

This module is intended to support
[Extensible Markup Language (XML) 1.1 (Second Edition)](https://www.w3.org/TR/2006/REC-xml11-20060816/),
but it is not fully supported at this time.

This module is not intended to support DOM API.

This module does not support XML namespace (xmlns).

## Values

### namespace Minilib.Encoding.Xml

#### escape_special

Type: `Std::String -> Std::String`

Escapes XML special characters.
eg. `&` -> `&amp;`, `<` -> `&lt;`, `>` -> `&gt;`, `\"` -> `&quot;`, `'` -> `&#039;`

#### unescape_special

Type: `Std::String -> Std::String`

Unescapes XML special characters.
eg. `&amp;` -> `&`, `&lt;` -> `<`, `&gt;` -> `>`, `&quot;` -> `\"`, `&#039;` -> `'`.
NOTE: Other character references is also converted.

### namespace Minilib.Encoding.Xml::XmlAttribute

#### make

Type: `Std::String -> Std::String -> Minilib.Encoding.Xml::XmlAttribute`

`XmlAttribute::make(name, value)` creates an attribute with the specified name and value.

### namespace Minilib.Encoding.Xml::XmlCDATASection

#### make

Type: `Std::String -> Minilib.Encoding.Xml::XmlCDATASection`

`XmlCDATASection::make(content)` creates a CDATA section with the specified content.
If `content` contains the end marker of CDATA section(`"]]>"`), this function panics.

### namespace Minilib.Encoding.Xml::XmlComment

#### make

Type: `Std::String -> Minilib.Encoding.Xml::XmlComment`

`XmlComment::make(content)` creates a comment node with the specified content.
If `content` contains a double-hyphen(`"--"`), this function panics.

### namespace Minilib.Encoding.Xml::XmlDeclaration

#### default

Type: `Minilib.Encoding.Xml::XmlDeclaration`

A default XML declaration with version="1.1", encoding="utf-8".

### namespace Minilib.Encoding.Xml::XmlDocument

#### add_to_epilog

Type: `Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlDocument -> Minilib.Encoding.Xml::XmlDocument`

Adds a child node to the epilog of the document.

#### add_to_prolog

Type: `Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlDocument -> Minilib.Encoding.Xml::XmlDocument`

Adds a child node to the prolog of the document.

#### empty

Type: `Minilib.Encoding.Xml::XmlDocument`

An empty XML document.

#### make

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlDocument`

Creates a XML document with the specified document element.

### namespace Minilib.Encoding.Xml::XmlElement

#### add

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.add(child)` adds a child element to `parent`.

#### addF

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.addF $ child` adds a child element to `parent`.
This is a flipped version of `add`.

#### add_node

Type: `Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`add_node` is synonym for `append_child`.

#### append_child

Type: `Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.append_child(child_node)` adds a child node to `parent`.

#### attr

Type: `Std::String -> Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`attr` is synonym for `set_attribute`.

#### concat_text_nodes

Type: `Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.concat_text_nodes` concats adjuscent text nodes.

#### element

Type: `Std::String -> Minilib.Encoding.Xml::XmlElement`

Synonym for `XmlElement::make`.

#### get_attribute

Type: `Std::String -> Minilib.Encoding.Xml::XmlElement -> Std::Option Std::String`

`element.get_attribute(name)` gets the value of a specified attribute
on the element.

#### make

Type: `Std::String -> Minilib.Encoding.Xml::XmlElement`

`XmlElement::make(tag_name)` creates an empty element with the specified tag name.

#### remove_attribute

Type: `Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.remove_attribute(name)` removes the attribute with the specified name
from the element. If the specified attribute does not exist, this function does nothing.

#### set_attribute

Type: `Std::String -> Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.set_attribute(name,value)` sets the value of an attribute
on the element.
If an attribute of same name exists, it will be replaced.
NOTE: validity of attribute names are not checked.

#### text

Type: `Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.text(content)` adds a text node to `element`.

### namespace Minilib.Encoding.Xml::XmlProcessingInstruction

#### make

Type: `Std::String -> Minilib.Encoding.Xml::XmlProcessingInstruction`

`XmlProcessingInstruction::make(content)` creates a processing instruction with the specified content.

### namespace Minilib.Encoding.Xml::XmlText

#### make

Type: `Std::String -> Minilib.Encoding.Xml::XmlText`

`XmlText::make(content)` creates a text node with the specified content.

## Types and aliases

### namespace Minilib.Encoding.Xml

#### XmlAttribute

Defined as: `type XmlAttribute = unbox struct { ...fields... }`

A type that represents name and value of an attribute.

##### field `name`

Type: `Std::String`

##### field `value`

Type: `Std::String`

#### XmlCDATASection

Defined as: `type XmlCDATASection = unbox struct { ...fields... }`

A type that represents a CDATA section.

##### field `content`

Type: `Std::String`

#### XmlComment

Defined as: `type XmlComment = unbox struct { ...fields... }`

A type that represents a comment node.

##### field `content`

Type: `Std::String`

#### XmlDeclaration

Defined as: `type XmlDeclaration = unbox struct { ...fields... }`

A type that represents an XML declaration.

##### field `version`

Type: `Std::String`

##### field `encoding`

Type: `Std::Option Std::String`

##### field `standalone`

Type: `Std::Option Std::String`

#### XmlDocument

Defined as: `type XmlDocument = box struct { ...fields... }`

A type that represents an XML document.

##### field `xml_decl`

Type: `Minilib.Encoding.Xml::XmlDeclaration`

##### field `prolog`

Type: `Std::Array Minilib.Encoding.Xml::XmlNode`

##### field `document_element`

Type: `Minilib.Encoding.Xml::XmlElement`

##### field `epilog`

Type: `Std::Array Minilib.Encoding.Xml::XmlNode`

#### XmlElement

Defined as: `type XmlElement = unbox struct { ...fields... }`

A type that represents an XML element.

##### field `tag_name`

Type: `Std::String`

##### field `attributes`

Type: `Std::Array Minilib.Encoding.Xml::XmlAttribute`

##### field `children`

Type: `Std::Array Minilib.Encoding.Xml::XmlNode`

#### XmlNode

Defined as: `type XmlNode = box union { ...variants... }`

A type that represents an XML node.
cf. [DOM: 4.4. Interface Node](https://dom.spec.whatwg.org/#node)

##### variant `element_node`

Type: `Minilib.Encoding.Xml::XmlElement`

##### variant `attribute_node`

Type: `Minilib.Encoding.Xml::XmlAttribute`

##### variant `text_node`

Type: `Minilib.Encoding.Xml::XmlText`

##### variant `cdata_section`

Type: `Minilib.Encoding.Xml::XmlCDATASection`

##### variant `processing_instruction`

Type: `Minilib.Encoding.Xml::XmlProcessingInstruction`

##### variant `comment_node`

Type: `Minilib.Encoding.Xml::XmlComment`

##### variant `document_node`

Type: `Minilib.Encoding.Xml::XmlDocument`

#### XmlProcessingInstruction

Defined as: `type XmlProcessingInstruction = unbox struct { ...fields... }`

A type that represents a processing instruction.

##### field `content`

Type: `Std::String`

#### XmlText

Defined as: `type XmlText = unbox struct { ...fields... }`

A type that represents a text node.

##### field `content`

Type: `Std::String`

## Traits and aliases

## Trait implementations

### impl `Minilib.Encoding.Xml::XmlAttribute : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlAttribute : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlCDATASection : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlCDATASection : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlComment : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlComment : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlDeclaration : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlDeclaration : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlDocument : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlDocument : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlElement : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlElement : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlNode : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlNode : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlProcessingInstruction : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlProcessingInstruction : Std::ToString`

### impl `Minilib.Encoding.Xml::XmlText : Std::Add`

### impl `Minilib.Encoding.Xml::XmlText : Std::Eq`

### impl `Minilib.Encoding.Xml::XmlText : Std::ToString`