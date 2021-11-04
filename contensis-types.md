# Contensis specific _types

## _image

This take the existing Contensis format of image into an `_image` type, and keeps the contents the same as a CMS image today.

### Example

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

***

## _imageArray

The `_imageArray` type represents a group of images defined by the _asset type. Assets follow their existing structure.

### Example

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

***

## _component

The `_component` type represents an existing Contensis component making the Canvas extendable beyond the standard types. Its definition is defined by it's existing structure.

### Example

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
