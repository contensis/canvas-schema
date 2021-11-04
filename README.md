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

## Standard _types

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

### _quote

The `_quote` type represents a quotation with an optional source and citation.

#### Validation

| Property | Value |
|:--|:--|
| text | required |
| source | optional, required |
| citation | optional |

#### Example

**Status**: ✅ Approved

```json
{
  "type": "_quote",
  "value": {
      "text": "Stay hungry stay foolish",
      "source": "Steve Jobs",
      "citation": "https://www.apple.com/stevejobs/"
    }
}
```

---

### _divider

The `_divider` type defines a dividing break in content, usually rendered as a form of horizontal rule. 

#### Example

**Status**: ✅ Approved

```json
{
  "type": "_divider"
  "value": null // could be removed??
}
```

> Ideally `value` should not be present but this currently aligns with our composed item definition of type, value pairs.

---

### _externalImage

The `_externalImage` type represents an image being served from an external URL e.g. hot linking to an image from Unsplash, rather than being served from the CMS.

#### Validation

| Property | Value |
|:--|:--|
| url | required |
| caption | optional |
| altText | optional, required, decorative |

#### Example

**Status**: ✅ Approved

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

### _panel

The `_panel` type represents a block of text which is emphasised in a document to draw attention to the reader. It combines a message and a `panelType` property to determine its visual style / emphasis type.

#### Validation

| Property | Required | Values |
|:--|:--|:--|
| title | optional | `string` |
| message | required | `string` or a `fragment` array |
| panelType | required | info (default), note, warning, positive, warning, info |

#### Example

**Status**: ✅ Approved

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

### _embed

The `_embed` type takes a URL of a service to generate a preview of the URL you pasted and can contain an optional `caption`. 

#### Validation

| Property | Required | Values |
|:--|:--|:--|
| url | required | `string` |
| caption | optional | `string` or a `fragment` array |

#### Example

**Status**: ✅ Approved

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

### _bookmark

The `_bookmark` type takes a URL and generates a bookmark card using [Open Graph](https://ogp.me/) metadata from the pasted URL.

#### Validation

| Property | Required | Values|
|:--|:--|:--|
| url | required | `string` |
| title | required | `string` |
| description | optional | `string` |
| imageUrl | optional | `string` |

#### Example

**Status**: ✅ Approved

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

## Contensis specific _types

### _image

This take the existing Contensis format of image into an `_image` type, and keeps the contents the same as a CMS image today.

#### Example

**Status**: ⚠️ Needs further discussion


```json
{
  "type": "_image",
  "value": {
    "asset": { AS PER CURRENT FORMAT },
    "caption": "A VW Beetle at the quayside",
    "altText": "beetle at the quayside",
    "transformations": null
  }
}
```

---

### _imageArray

The `_imageArray` type represents a group of images defined by the _asset type. Assets follow their existing structure.

#### Example

**Status**: ⚠️ Needs further discussion

```json
{
  "type": "_imageArray",
  "value": [{
     "_asset": {
        "altText": "An example image",
        "sys": { Existing definition},
      "caption": "",
      "altText": "Image one",
      "transformations": null
    },
    "_asset": {
        "altText": "An example image",
        "sys": { Existing definition},
      "caption": "",
      "altText": "Image two",
      "transformations": null
    },
    "_asset": {
        "altText": "An example image",
        "sys": { Existing definition},
      "caption": "",
      "altText": "Image three",
      "transformations": null
    },
  }]
}
```

---

### _component

The `_component` type represents an existing Contensis component making the Canvas extendable beyond the standard types. Its definition is defined by it's existing structure.

#### Example

**Status**: ⚠️ Needs further discussion

```json
{
  "type": "_component",
  "value": {
    THIS WOULD BE THE COMPONENT IN CONTENSIS TODAY
  },
  "properties": {
    "componentId": "address"
  }
}
```

---

## _type rules

- When the value is a simple string without any decorators there is no reason to store them as arrays of fragments (This make it easier to read and reduces the storage required)

## Decorators

Decorators are applied to `_fragments` to describe and define the text to give it richness. Decorators are defined as arrays within the properties object of a `_fragment`. Decorators can be paired with their own property object to extend their definition. As seen in the link decorator.

### Supported decorators

#### strong

The `strong` decorator is used to define text with strong importance. Typically used to give text a bold appearance.

```md
**Important** Make sure you wear safety goggles.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Important",
      "properties": {
        "decorators": ["strong"]
      }
    },
    {
      "type": "_fragment",
      "value": "Make sure you wear safety goggles"
    }
  ]
}
```

#### emphasis

The `emphasis` decorator is used to stress emphasis. Typically used to give text an italic appearance.

```md
This is _not_ a drill.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is "
    },
    {
      "type": "_fragment",
      "value": "not",
      "properties": {
        "decorators": ["emphasis"]
      }
    },
    {
      "type": "_fragment",
      "value": " a drill"
    }
  ]
}
```

#### underline (deprecate?)

#### strikethrough

The `strikethrough` decorator represents a `_fragment` that is no longer relevant or no longer accurate.

```md
My favourite species of ~~flamingo is the Lesser flamingo Andean flamingo~~ Chilean flamingo.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "My favourite species of flamingo is the "
    },
    {
      "type": "_fragment",
      "value": "Lesser flamingo Andean flamingo",
      "properties": {
        "decorators": ["strikethrough"]
      }
    },
    {
      "type": "_fragment",
      "value": " Chilean flamingo."
    }
  ]
}
```

#### subscript

The `subscript` decorator specifies a `_fragment` that is to be displayed as subscript solely for typographical reasons.

```md
Almost every developer's favourite molecule is C~8~H~10~N~4~O~2~, also known as "caffeine."
```

```json
[
    {
      "type": "_paragraph",
      "value": [
        {
          "type": "_fragment",
          "value": "Almost every developer's favourite molecule is C"
        },
        {
          "type": "_fragment",
          "value": "8",
          "properties": {
            "decorators": [
              "subscript"
            ]
          }
        },
        {
          "type": "_fragment",
          "value": "H"
        },
        {
          "type": "_fragment",
          "value": "10",
          "properties": {
            "decorators": [
              "subscript"
            ]
          }
        },
        {
          "type": "_fragment",
          "value": "N"
        },
        {
          "type": "_fragment",
          "value": "4",
          "properties": {
            "decorators": [
              "subscript"
            ]
          }
        },
        {
          "type": "_fragment",
          "value": "O"
        },
        {
          "type": "_fragment",
          "value": "2",
          "properties": {
            "decorators": [
              "subscript"
            ]
          }
        },
        {
          "type": "_fragment",
          "value": ", also known as \"caffeine\"."
        }
      ]
    }
  ]
```

#### superscript

The `superscript` decorator specifies a `_fragment` that is to be displayed as superscript solely for typographical reasons.

```md
H^2^O
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "H"
    },
    {
      "type": "_fragment",
      "value": "2",
      "properties": {
        "decorators": ["superscript"]
      }
    },
    {
      "type": "_fragment",
      "value": "O"
    }
  ]
}
```

#### mark

The `mark` decorator represents a `_fragment` which is marked or highlighted for reference or notation purposes.

```md
Several species of <mark>salamander</mark> inhabit the temperate rainforest of the Pacific Northwest.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Several species of "
    },
    {
      "type": "_fragment",
      "value": "salamander",
      "properties": {
        "decorators": [
          "mark"
        ]
      }
    },
    {
      "type": "_fragment",
      "value": " inhabit the temperate rainforest of the Pacific Northwest."
    }
  ]
}
```

#### code

The `code` decorator indicates that the `_fragment` is a short piece of computer code.

```md
The `.header` class defines the CSS selector to style the header component. 
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "The "
    },
    {
      "type": "_fragment",
      "value": ".header",
      "properties": {
        "decorators": ["code"]
      }
    },
    {
      "type": "_fragment",
      "value": " class defines the CSS selector to style the header component. "
    }
  ]
}
```

#### keyboard

The `keyboard` decorator indicates a `_fragment` denoting textual user input from a keyboard.

```md
Press ===Ctrl+Shift+C=== to mark the selection as inline code
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Press "
    },
    {
      "type": "_fragment",
      "value": "Ctrl+Shift+C",
      "properties": {
        "decorators": ["keyboard"]
      }
    },
    {
      "type": "_fragment",
      "value": " to mark the selection as inline code"
    }
  ]
}
```

#### variable

The `variable` decorator represents the name of a variable in a mathematical expression or a programming context.

```md
The volume of a box is <var>l</var> × <var>w</var> × <var>h</var>
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "The volume of a box is "
    },
    {
      "type": "_fragment",
      "value": "l",
      "properties": {
        "decorators": ["variable"]
      }
    },
    {
      "type": "_fragment",
      "value": " × "
    },
    {
      "type": "_fragment",
      "value": "w",
      "properties": {
        "decorators": ["variable"]
      }
    },
    {
      "type": "_fragment",
      "value": " × "
    },
    {
      "type": "_fragment",
      "value": "h",
      "properties": {
        "decorators": ["variable"]
      }
    }
  ]
}
```

#### insert

The `insert` decorator represents a `_fragment` that has been added to a document.

```md
<ins>This sentence has been added.</ins>
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This sentence has been added.",
      "properties": {
        "decorators": ["insert"]
      }
    }
  ]
}
```

#### delete

The `delete` decorator represents a `_fragment` that has been deleted from a document.

```md
<ins>This sentence has been deleted.</ins>
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This sentence has been deleted.",
      "properties": {
        "decorators": ["delete"]
      }
    }
  ]
}
```

#### link

The `link` decorator is composed of two parts. It contains the decorator property of `link`, but is also paired with is own link object attached to the properties object of the `_fragment` to include elements such as the link URL.

```md
This is a [link](https://www.bbc.co.uk) to the BBC.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is a "
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
      "value": " to the BBC"
    }
  ]
}
```

## Further discussion / comments

1. What languages do we want to support from the initial implementation of the _code type.
2. Do we want to name the `_heading` type `_heading` or `_header`
3. Do we want to name the `level` property of the `_heading` type `headingType` to be consistent with the other types?
4. I changed the decorators from `strong` | `emphasis` to `bold` | `italic` and then back again, as bold and italic refer to more visual styling than describing the intent of the formatting.
5. I've added `_tableCaption` to our table definition as we should support accessible tables from the outset.
6. Should `_tableCells` support both `string` and `fragments`
7. Should we change remove underline decorator, the `<u>` element should not be used to format `underlined` text in HTML and doing so in the Canvas may suggest that is correct understanding of the `<u>` element as per [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/u)
