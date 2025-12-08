# Minilib.Encoding.Xml.XmlHelpers

Defined in minilib-xml@0.5.3

XML helpers, such as escaping/unescaping special characters.

## Values

### namespace Minilib.Encoding.Xml.XmlHelpers

#### escape_special

Type: `Std::String -> Std::String`

Escapes XML special characters.
eg. `&` -> `&amp;`, `<` -> `&lt;`, `>` -> `&gt;`, `\"` -> `&quot;`, `'` -> `&#039;`

#### unescape_special

Type: `Std::String -> Std::String`

Unescapes XML special characters.
eg. `&amp;` -> `&`, `&lt;` -> `<`, `&gt;` -> `>`, `&quot;` -> `\"`, `&#039;` -> `'`.
NOTE: Other character references is also converted.

## Types and aliases

## Traits and aliases

## Trait implementations