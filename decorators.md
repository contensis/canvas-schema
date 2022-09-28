# Decorators

Decorators are applied to `_fragments` to describe and define the text to give it richness. Decorators are defined as arrays within the properties object of a `_fragment`. Decorators can be paired with their own property object to extend their definition. As seen in the link decorator.

## Supported decorators

### strong

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

### emphasis

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

### strikethrough

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

### subscript

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

### superscript

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

### mark

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

### code

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

### keyboard

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

### variable

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

### insert

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

### delete

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

### link

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

### Anchor

The `anchor` decorator is composed of two parts. It contains the decorator property of `anchor`, but is also paired with is own anchor object attached to the properties object of the `_fragment` to include elements such as the ID.

```md
This is an [anchor](#my-heading-anchor) in the middle of a paragraph.
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is an "
    },
    {
      "type": "_fragment",
      "value": "anchor",
      "properties": {
        "anchor": {
          "id": "#my-heading-anchor"
        },
        "decorators": ["anchor"]
      }
    },
    {
      "type": "_fragment",
      "value": " in the middle of a paragraph."
    }
  ]
}
```

### linebreak

The `linebreak` decorator represents a soft return in a paragraph of text.

```txt
This is a sentence and a soft
return has been added
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "This is a sentence and a soft"
    },
    {
      "type": "_fragment",
      "value": " ", // this is a carriage return
      "properties": {
        "decorators": ["linebreak"]
      }
    },
    {
      "type": "_fragment",
      "value": "return has been added"
    }
  ]
}
```

### Comment

The `comment` decorator can be applied to a `_fragment` or directly on a `_type` so that another user can respond or take action on a piece of content.

#### Comment `_fragment` example

```txt
The capital of England is Cardiff.
```

In this example the word Cardiff is marked with a comment needing to be corrected by the author to London.

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "The capital of England is "
    },
    {
      "type": "_fragment",
      "value": "Cardiff",
      "properties": {
        "decorators": ["comment"],
        "comment": {
          "commentId": "0000-1234-5678-9101-1121",
          "authorId": "BC12-1234-5678-9101-1121"
        }
      }
    }
  ]
}
```

#### Comment `_type` example

In this example the `_code` type has a comment added to it.

```json
{
  "type": "_code",
  "value": {
    "code": "console.log(\"hello world\");",
    "language": "javascript",
    "caption": "Hello World shown in JavaScript"
  },
  "properties": {
    "comment": {
      "commentId": "0000-1234-5678-9101-1121",
      "authorID": "BC12-1234-5678-9101-1121"
    }
  }
}
```
