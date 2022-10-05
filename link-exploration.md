## Hyperlink to a node or hyperlink to an entry

As an author, I want to create a hyperlink to some CMS content, either by selecting an entry with a URL or a node in the Site View tree, with the intent of this content being rendered in a web page.

```md
This is a [link](node: 1234) to the Contensis product page.
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
          "node": "1234",
          "entryId: "0000-0000-0000-0000",
          "url": "/products/contensis",
          "newTab": false // property name to be decided on
        },
        "decorators": ["link"]
      }
    },
    {
      "type": "_fragment",
      "value": " to the Contensis product page."
    }
  ]
}
```

## Link to an external URL

As an author, I want to create a hyperlink to an external website that opens in a new tab so that I can reference some external content.

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
          "url": "http://www.bbc.co.uk",
          "newTab": false // property name to be decided on
        },
        "decorators": ["link"]
      }
    },
    {
      "type": "_fragment",
      "value": " to the BBC."
    }
  ]
}
```

## Link to an anchor

// Anchor decorator needs discussing

## Inline entry embed

As an author, I want to embed an inline entry into my canvas so that my content can be dynamically generated based on the content of another entry.

> Effectively, you are @mentioning an entry and using its title to be displayed in the canvas.

As an author, I want to be able to click through my dynamic content on a canvas so that I can see the content in its entirety.

> Generate the content from the title field of the entry

```txt
The CEO is {Person: Richard Chivers}
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "The CEO is "
    },
    {
      "type": "_inline-entry", // Special fragment?
      "value": {
        "sys": { Standard sysObject},
        "entryTitle": "Richard Chivers",
        "entryDescription": "Richard is the founder and CEO of Zengenti",
        "entryThumbnail": null
      }
    }
  ]
}
```

> Generate the content from the title field of the entry

```txt
Our latest printer {Product: HP 5000 series}
```

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Our latest printer is "
    },
    {
      "type": "_inline-entry", // Special fragment?
      "value": {
        "sys": { Standard sysObject},
        "entryTitle": "HP 5000 series",
        "entryDescription": null,
        "entryThumbnail": null
      }
    }
  ]
}
```

## Inline asset embed

As an author, I want to insert a link to an asset so that the content can be downloaded or referenced on my front-end site.

> Effectively, you are @mentioning an asset and using its title to be displayed in the canvas.

As an author, I want to click through my dynamic asset content on a canvas to see the content in its entirety. e.g. Open it in the asset editor.

```json
{
  "type": "_paragraph",
  "value": [
    {
      "type": "_fragment",
      "value": "Download the printers "
    },
    {
      "type": "_inline-asset", // Special fragment?
      "value": {
        "sys": { Standard sysObject},
        "entryTitle": "Technical Manual HP 5000 Series",
        "entryDescription": null,
        "entryThumbnail": null
      }
    }
  ]
}
```

## Entry

As an author, I want to insert an entry into my canvas so that the content can be rendered at the point of insertion on my front-end site.

```json
{
  "type": "_entry",
  "value": {
    "sys": { Standard sysObject},
    "entryTitle": "Eric Carle",
    "entryDescription": "An author who wrote some children's books",
    "entryThumbnail": null
  }
}
```


## Form

As an author, I want to insert a form into my canvas so that the form fields can be rendered at the point of insertion on my front-end site.

```json
{
  "type": "_form",
  "value": {
    "sys": { Standard sysObject},
    "formTitle": "Contact us",
  }
}
```

## Asset

As an author, I want to insert an answer into my canvas so that the content can be rendered at the point of insertion on my front-end site.

```json
{
    "type": "_asset",
    "value": {
    "sys": { Standard sysObject},
        "entryTitle": "Largest-living-cat",
        "entryDescription": null,
        "entryThumbnail": null,
    }
}
```
