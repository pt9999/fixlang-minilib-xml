# `module Minilib.Encoding.Xml`

Simple XML Model.

This module is intended to support
[Extensible Markup Language (XML) 1.1 (Second Edition)](https://www.w3.org/TR/2006/REC-xml11-20060816/),
but it is not fully supported at this time.

This module is not intended to support DOM API.

This module does not support XML namespace (xmlns).

# Types and aliases

## `namespace Minilib.Encoding.Xml`

### `type XmlAttribute = unbox struct { ...fields... }`

A type that represents name and value of an attribute.

#### field `name : Std::String`

#### field `value : Std::String`

### `type XmlCDATASection = unbox struct { ...fields... }`

A type that represents a CDATA section.

#### field `content : Std::String`

### `type XmlComment = unbox struct { ...fields... }`

A type that represents a comment node.

#### field `content : Std::String`

### `type XmlDeclaration = unbox struct { ...fields... }`

A type that represents an XML declaration.

#### field `version : Std::String`

#### field `encoding : Std::Option Std::String`

#### field `standalone : Std::Option Std::String`

### `type XmlDocument = box struct { ...fields... }`

A type that represents an XML document.

#### field `xml_decl : Minilib.Encoding.Xml::XmlDeclaration`

#### field `prolog : Std::Array Minilib.Encoding.Xml::XmlNode`

#### field `document_element : Minilib.Encoding.Xml::XmlElement`

#### field `epilog : Std::Array Minilib.Encoding.Xml::XmlNode`

### `type XmlElement = unbox struct { ...fields... }`

A type that represents an XML element.

#### field `tag_name : Std::String`

#### field `attributes : Std::Array Minilib.Encoding.Xml::XmlAttribute`

#### field `children : Std::Array Minilib.Encoding.Xml::XmlNode`

### `type XmlNode = box union { ...variants... }`

A type that represents an XML node.
cf. [DOM: 4.4. Interface Node](https://dom.spec.whatwg.org/#node)

#### variant `element_node : Minilib.Encoding.Xml::XmlElement`

#### variant `attribute_node : Minilib.Encoding.Xml::XmlAttribute`

#### variant `text_node : Minilib.Encoding.Xml::XmlText`

#### variant `cdata_section : Minilib.Encoding.Xml::XmlCDATASection`

#### variant `processing_instruction : Minilib.Encoding.Xml::XmlProcessingInstruction`

#### variant `comment_node : Minilib.Encoding.Xml::XmlComment`

#### variant `document_node : Minilib.Encoding.Xml::XmlDocument`

### `type XmlProcessingInstruction = unbox struct { ...fields... }`

A type that represents a processing instruction.

#### field `content : Std::String`

### `type XmlText = unbox struct { ...fields... }`

A type that represents a text node.

#### field `content : Std::String`

# Traits and aliases

# Trait implementations

### `impl Minilib.Encoding.Xml::XmlAttribute : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlAttribute : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlCDATASection : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlCDATASection : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlComment : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlComment : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlDeclaration : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlDeclaration : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlDocument : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlDocument : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlElement : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlElement : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlNode : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlNode : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlProcessingInstruction : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlProcessingInstruction : Std::ToString`

### `impl Minilib.Encoding.Xml::XmlText : Std::Add`

### `impl Minilib.Encoding.Xml::XmlText : Std::Eq`

### `impl Minilib.Encoding.Xml::XmlText : Std::ToString`

# Values

## `namespace Minilib.Encoding.Xml`

### `escape_special : Std::String -> Std::String`

Escapes XML special characters.
eg. `&` -> `&amp;`, `<` -> `&lt;`, `>` -> `&gt;`, `\"` -> `&quot;`, `'` -> `&#039;`

### `unescape_special : Std::String -> Std::String`

Unescapes XML special characters.
eg. `&amp;` -> `&`, `&lt;` -> `<`, `&gt;` -> `>`, `&quot;` -> `\"`, `&#039;` -> `'`.
NOTE: Other character references is also converted.

## `namespace Minilib.Encoding.Xml::XmlAttribute`

### `_sort_by_name : Std::Array Minilib.Encoding.Xml::XmlAttribute -> Std::Array Minilib.Encoding.Xml::XmlAttribute`

`attributes._sort_by_name` sorts an array of attributes by the name.

### `make : Std::String -> Std::String -> Minilib.Encoding.Xml::XmlAttribute`

`XmlAttribute::make(name, value)` creates an attribute with the specified name and value.

## `namespace Minilib.Encoding.Xml::XmlCDATASection`

### `make : Std::String -> Minilib.Encoding.Xml::XmlCDATASection`

`XmlCDATASection::make(content)` creates a CDATA section with the specified content.
If `content` contains the end marker of CDATA section(`"]]>"`), this function panics.

## `namespace Minilib.Encoding.Xml::XmlComment`

### `make : Std::String -> Minilib.Encoding.Xml::XmlComment`

`XmlComment::make(content)` creates a comment node with the specified content.
If `content` contains a double-hyphen(`"--"`), this function panics.

## `namespace Minilib.Encoding.Xml::XmlDeclaration`

### `default : Minilib.Encoding.Xml::XmlDeclaration`

A default XML declaration with version="1.1", encoding="utf-8".

## `namespace Minilib.Encoding.Xml::XmlDocument`

### `add_to_epilog : Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlDocument -> Minilib.Encoding.Xml::XmlDocument`

Adds a child node to the epilog of the document.

### `add_to_prolog : Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlDocument -> Minilib.Encoding.Xml::XmlDocument`

Adds a child node to the prolog of the document.

### `empty : Minilib.Encoding.Xml::XmlDocument`

An empty XML document.

### `make : Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlDocument`

Creates a XML document with the specified document element.

## `namespace Minilib.Encoding.Xml::XmlElement`

### `add : Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.add(child)` adds a child element to `parent`.

### `addF : Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.addF $ child` adds a child element to `parent`.
This is a flipped version of `add`.

### `add_node : Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`add_node` is synonym for `append_child`.

### `append_child : Minilib.Encoding.Xml::XmlNode -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`parent.append_child(child_node)` adds a child node to `parent`.

### `attr : Std::String -> Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`attr` is synonym for `set_attribute`.

### `concat_text_nodes : Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.concat_text_nodes` concats adjuscent text nodes.

### `element : Std::String -> Minilib.Encoding.Xml::XmlElement`

Synonym for `XmlElement::make`.

### `get_attribute : Std::String -> Minilib.Encoding.Xml::XmlElement -> Std::Option Std::String`

`element.get_attribute(name)` gets the value of a specified attribute
on the element.

### `make : Std::String -> Minilib.Encoding.Xml::XmlElement`

`XmlElement::make(tag_name)` creates an empty element with the specified tag name.

### `remove_attribute : Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.remove_attribute(name)` removes the attribute with the specified name
from the element. If the specified attribute does not exist, this function does nothing.

### `set_attribute : Std::String -> Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.set_attribute(name,value)` sets the value of an attribute
on the element.
If an attribute of same name exists, it will be replaced.
NOTE: validity of attribute names are not checked.

### `text : Std::String -> Minilib.Encoding.Xml::XmlElement -> Minilib.Encoding.Xml::XmlElement`

`element.text(content)` adds a text node to `element`.

## `namespace Minilib.Encoding.Xml::XmlProcessingInstruction`

### `make : Std::String -> Minilib.Encoding.Xml::XmlProcessingInstruction`

`XmlProcessingInstruction::make(content)` creates a processing instruction with the specified content.

## `namespace Minilib.Encoding.Xml::XmlText`

### `make : Std::String -> Minilib.Encoding.Xml::XmlText`

`XmlText::make(content)` creates a text node with the specified content.