---
version: Working draft
authors:
	- Scott Yearsley
	- Richard Saunders
	- Dan White
---

# Contensis canvas specification

**Version**: Working Draft

***

## Description

## Terminology

| Term | Definition |
|:--|:--|
| _types | String |
| Fragments | Array |
| Decorators | Array |
| Properties | Any metadata that describes the type and can be used to set the rendering intent in the Canvas editor or when consumed via the API. |

## Supported types

[_paragraph](standard-types.md#_paragraph)
[_paragraph](standard-types.md#_paragraph)


### _type rules

- When the value is a simple string without any decorators there is no reason to store them as arrays of fragments (This make it easier to read and reduces the storage required)

## Further discussion / comments

1. What languages do we want to support from the initial implementation of the _code type.
2. Do we want to name the `_heading` type `_heading` or `_header`
3. Do we want to name the `level` property of the `_heading` type `headingType` to be consistent with the other types?
4. I changed the decorators from `strong` | `emphasis` to `bold` | `italic` and then back again, as bold and italic refer to more visual styling than describing the intent of the formatting.
5. I've added `_tableCaption` to our table definition as we should support accessible tables from the outset.
6. Should `_tableCells` support both `string` and `fragments`
7. Should we change remove underline decorator, the `<u>` element should not be used to format `underlined` text in HTML and doing so in the Canvas may suggest that is correct understanding of the `<u>` element as per [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/u)
