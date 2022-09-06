# Search fields

The following values of the canvas items described by the following tables should be searchable when carrying out a freeText search.

## Standard types

| Type | Search |
|:--|:--|
| [_paragraph](standard-types.md#_paragraph)| value/fragment values |
| [_heading](standard-types.md#_heading)| value/fragment values |
| [_list](standard-types.md#_list)| value/fragment values |
| [_code](standard-types.md#_code)| `code`, `caption` |
| [_table](standard-types.md#_table)| `tableCaption` value/fragment values, `tableCell` value/fragment values, `tableHeaderCell` value/fragment values |
| [_quote](standard-types.md#_quote)| value/fragment values, `source`, `citation` |
| [_divider](standard-types.md#_divider)| - |
| [_panel](standard-types.md#_panel)| value/fragment values, `title` |
| [_embed](standard-types.md#_embed)| `url`, `caption` |
| [_bookmark](standard-types.md#_bookmark)| `url`, `title`, `description` |

## Contensis types

| Type | Status |
|:--|:--|
| [_image](contensis-types.md#_image)| `url(external)`, `caption`, `altText` |
| [_imageArray](contensis-types.md#_imageArray)| `url(external)`, `caption`, `altText` |
| [_component](contensis-types.md#_component)| displayTitle (when implemented) |

