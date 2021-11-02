---
version: Working draft
authors:
	- Scott Yearsley
	- Richard Saunders
	- Dan White
---

# Contensis canvas specification  
**Version**: Working Draft

---

{{TOC}}

## Description
## Terminology

| Term | Definition |
|:--|:--|
| _types | String |
| Fragments | Array |
| Decorators | Array |
| Properties | Any metadata that describes the type and can be used to set the rendering intent in the Canvas editor or when consumed via the API. |



## Supported _types

### _paragraph 
The `_paragraph` type represents a standard block of text, either as plain text or formatted text using fragments and decorators. A `_paragraph` can be either a `string` or a `fragment` array.

#### Properties

| Property | Value |
|:--|:--|
| paragraphType | none (default), lede |

#### Validation
**Lede** – there can only be a single lede paragraph in a canvas.

#### Examples

##### Plain text paragraph

**Status**: ✅ Approved

```md
This is a paragraph
```

```json
{
  "type": "_paragraph",
  "value": "This is a paragraph"
}
```

##### Paragraph with text formatting

**Status**: ✅ Approved

```md
This is some **bold** _text_
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is some "
    },
    {
      "type": "_fragment",
      "value": "strong",
      "properties": {
        "decorators": ["strong"]
      }
    },
    {
      "type": "_fragment",
      "value": " "
    },
    {
      "type": "_fragment",
      "value": "text",
      "properties": {
        "decorators": ["emphasis"]
      }
    }
  ]
}
```

##### Paragraph with link

**Status**: ✅ Approved

```md
Check out our latest [Boston Fern](https://www.leif.com/plants/boston-fern) plant
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Check out our latest "
    },
    {
      "type": "_fragment",
      "value": "Boston Fern",
      "properties": {
        "link": {
          "url": "https://www.leif.com/plants/boston-fern"
        },
        "decorators": ["link"]
      }
    },
    {
      "type": "_fragment",
      "value": " Plant"
    }
  ]
}
```

##### Paragraph with separated inline styles

**Status**: ✅ Approved

```md
This is some **bold** **text**
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is some "
    },
    {
      "type": "_fragment",
      "value": "strong"
      "properties": {
        "decorators": ["strong"]
      },
    },
    {
      "type": "_fragment",
      "value": " "
    },
    {
      "type": "_fragment",
      "value": "text"
      "properties": {
        "decorators": ["strong"]
      },
    }
  ]
}
```

> **Note:** If the space is deleted between the two fragments in this instance then the fragments will be merged.

##### Paragraph with nested fragments

**Status**: ✅ Approved

```md
This is a sentence that **has a [link](https://www.contensis.com) that is bold**
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is a sentence that "
    },
    {
      "type": "_fragment",
      "value": [
        {
          "type": "_fragment",
          "value": "has a "
        },
        {
          "type": "_fragment",
          "value": "link",
          "properties": {
            "link": {
              "url": "https://www.bbc.co.uk"
            },
            "decorators": ["link"]
          }
        },
        {
          "type": "_fragment",
          "value": " that is bold"
        }
      ],
      "properties": {
        "decorators": ["strong"]
      }
    }
  ]
}
```

##### Lede paragraph

**Status**: ✅ Approved

Represents a lede introductory paragraph.

```md
This is a lede paragraph
```

```json
{
  "type": "_paragraph",
  "value": "This is a paragraph",
  "properties": {
    "paragraphType": "lede"
  }
}
```

---
### _heading
A `_heading` represents a block of text that is used as a section header, it has a `level` property to set the hierarchy of the header. A `_heading` can be either a `string` or a `fragment` array.

#### Properties
| Property | Value |
|:--|:--|
| level | 1 (default), 2, 3, 4, 5, 6 |

#### Examples

##### Simple heading

**Status**: ✅ Approved

```md
# This is my heading
```

```json
{
  "type": "_heading",
  "value": "This is my heading",
  "properties": {
    "level": 1
  }
}
```


##### Heading with inline styles

**Status**: ✅ Approved

```md
# This *is* my heading
```

```json
{
  "type": "_heading",
  "value": [
    {
      "type": "_fragment",
      "value": "This "
    },
    {
      "type": "_fragment",
      "value": "is",
      "properties": {
        "decorators": ["emphasis"]
      }
    },
    {
      "type": "_fragment",
      "value": " my heading"
    }
  ],
  "properties": {
    "level": 1
  }
}
```

---

### _list
A `_list` represents a flat or nested list of content. Each item in a list is represented by a `_listItem` type. A `_listItem` can be either a `string` or a `fragment` array.

#### Properties
| Property | Value |
|:--|:--|
| listType | unordered (default), ordered |

#### Examples

##### Unordered list

**Status**: ✅ Approved

```md
- **_List item one_**
- List item two
- **List item three**
```

```json
{
  "type": "_list",
  "value": [
    {
      "type": "_listItem",
      "value": [
        {
          "type": "_fragment",
          "value": "List item one",
          "properties": {
            "decorators": ["strong", "emphasis"]
          }
        }
      ]
    },
    {
      "type": "_listItem",
      "value": "List item two"
    },
    {
      "type": "_listItem",
      "value": [
        {
          "type": "_fragment",
          "value": "List item three",
          "properties": {
            "decorators": ["strong"]
          }
        }
      ]
    }
  ],
  "properties": {
    "listType": "unordered"
  }
}

```

##### Ordered list

**Status**: ✅ Approved

```md
1. **_List item one_**
2. List item two
3. **List item three**
```

```json
{
  "type": "_list",
  "value": [
    {
      "type": "_listItem",
      "value": [
        {
          "type": "_fragment",
          "value": "List item one",
          "properties": {
            "decorators": ["strong", "emphasis"]
          }
        }
      ]
    },
    {
      "type": "_listItem",
      "value": "List item two"
    },
    {
      "type": "_listItem",
      "value": [
        {
          "type": "_fragment",
          "value": "List item three",
          "properties": {
            "decorators": ["strong"]
          }
        }
      ]
    }
  ],
  "properties": {
    "listType": "ordered"
  }
}
```

---

### _code
The `_code` type represents a code example, with an optional `language` property which controls how the code should be displayed at render.

#### Properties
| Property | Value |
|:--|:--|
| language | list of language names supported by [prism](https://prismjs.com/#supported-languages) or similar FE framework |

#### Example

**Status**: ✅ Approved

> We took this approach on Code, to be consistent with our headings, paragraph and lists which use properties to control its display type.

```json
{
  "type": "_code",
  "value": "console.log(\"hello world\");",
  "properties": {
    "language": "javascript"
  }
}
```

---

### _table
The `_table` type represents a table of data, a `_table` is broken up into a table caption (`_tableCaption`) table header (`_tableHeader`) and a table body (`_tableBody`), which in turn contains table rows (`_tableRow`) of which support table header cells (`_tableHeaderCell`) and table cells (`_tableCell`).

#### Validation
| Property | Value | Description|
|:--|:--|:--|
| `_table` | Supports `_tableCaption`, `_tableHeader` and `_tableBody`  | Provides the wrapping type for a table |
| `_tableCaption` | Can be either a `string` or a `fragment` array.| Defines a the table caption `<caption>` in HTML |
| `_tableHeader` | Supports `_tableRow` | Provides the definition of a `<thead>` element in HTML |
| `_tableBody` | Supports `_tableRow` | Provides the definition of a `<tbody>` element in HTML |
| `_tableRow` | Supports `_tableCell` and `_tableHeaderCell`| Defines a row of data in the table `<tr>` in HTML |
| `_tableCell` | Can be either a `string` or a `fragment` array.| Defines a the data of a cell `<td>` in HTML |
| `_tableHeaderCell` | Can be either a `string` or a `fragment` array.| Defines a the cell header `<th>` in HTML |


#### Example

**Status**: ⚠️ Needs further discussion

```json
{
  "type": "_table",
  "value": [
    {
      "type": "_tableCaption",
      "value": "This is the caption for the table"
    },
    {
      "type": "_tableHeader",
      "value": [
        {
          "type": "_tableRow",
          "value": [
            {
              "type": "_tableHeaderCell",
              "value": "Header"
            },
            {
              "type": "_tableHeaderCell",
              "value": "Header"
            }
          ]
        }
      ]
    },
    {
      "type": "_tableBody",
      "value": [
        {
          "type": "_tableRow",
          "value": [
            {
              "type": "_tableCell",
              "value": "Cell 1-1"
            },
            {
              "type": "_tableCell",
              "value": "Cell 1-2"
            }
          ]
        },
        {
          "type": "_tableRow",
          "value": [
            {
              "type": "_tableCell",
              "value": "Cell 2-1"
            },
            {
              "type": "_tableCell",
              "value": "Cell 2-2"
            }
          ]
        }
      ]
    }
  ]
}
```

### Panel
The `_panel` type represents a block of text which is emphasised in a document to draw attention to the reader. It combines a message and a `panelType` property to determine its visual style / emphasis type.

#### Validation

| Property | Required | Values|
|:--|:--|
| title | optional | `string` |
| message | required | `string` or a `fragment` array |
| panelType | required | info (default), note, warning, positive, warning, info |

#### Example

```json
{
  "type": "_panel",
  "value": {
    "title": "Heading",
    "message": "This is a call out message",
    "panelType": "note | warning | positive | negative | info"
  },
}
```

---

### Embed

The `_embed` type takes a URL of a service to generate a preview of the URL you pasted and can contain an optional `caption`. 

#### Validation

| Property | Required | Values|
|:--|:--|
| url | required | `string` |
| caption | optional | `string` or a `fragment` array |

#### Example
```json
{
  "type": "_embed",
  "value": {
    "url": "https://www.youtube.com/watch?v=ArOMXELHiLw",
    "caption": "An overview video of the Contensis CMS"
  }
}
```

---

### Bookmark

The `_bookmark` type takes a URL and generates a bookmark card using [Open Graph](https://ogp.me/) metadata from the pasted URL.

#### Validation

| Property | Required | Values|
|:--|:--|
| url | required | `string` |
| title | required | `string` |
| description | optional | `string` |
| imageUrl | optional | `string` |

#### Example
```json
{
  "type": "_bookmark",
  "value": {
    "url": "https://www.contensis.com",
    "title": "Contensis - enterprise web content management system (CMS)",
    "description": "The Contensis CMS powers the websites of some of the world's leading organisations. It's flexible, scalable, and easy to use.",
    "imageUrl": "https://www.contensis.com/static/img/contensis-placeholder.jpg?eacb14cab0cf966e14750eb3b927bf99"
  }
}
```

---

### Component

---

### Quote

---

### Image

---

### External image
The `_externalImage` type represents an image being served from an external URL e.g. hot linking to an image from Unsplash, rather than being served from the CMS.

#### Validation

| Property | Value |
|:--|:--|
| url | required |
| caption | optional |
| altText | optional, required, decorative |

#### Example
```json
{
  "type": "_externalImage",
  "value": {
    "url": "https://unsplash.com/photos/TYQ6fyF3Amc",
    "caption": "Photo by Jimmy Dean on Unsplash",
    "altText": "Man in white and orange long sleeve shirt holding chopsticks"
  }
}
```

---

## _type rules
- When the value is a simple string without any decorators there is no reason to store them as arrays of fragments (This make it easier to read and reduces the storage required)

## Decorators




## Further discussion / comments

1. What languages do we want to support from the initial implementation of the _code type.
2. Do we want to name the `_heading` type `_heading` or `_header`
3. Do we want to name the `level` property of the `_heading` type `headingType` to be consistent with the other types?
4. I changed the decorators from `strong` | `emphasis` to `bold` | `italic` and then back again, as bold and italic refer to more visual styling than describing the intent of the formatting.
5. I've added `_tableCaption` to our table definition as we should support accessible tables from the outset.
6. Should `_tableCells` support both `string` and `fragments`
