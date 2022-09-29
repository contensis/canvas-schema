# Contensis specific _types

## _image

This takes the existing Contensis format of image into an `_image` type, and keeps the contents the same as a CMS image today.

### Examples

#### Management API: External URL

```json
    {
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "url": "http://www.bbc.co.uk/images/boris_johnson.jpg",
            "altText": "Boris Johnson",
            "caption": "Boris Johnson resigns as PM"
        }
    }
 ```

#### Management API: CMS Image

```json
 {
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "asset": {
                "sys": {
                    "id": "e57979ef-2b86-45e3-8d37-1a744ba2ce7a"
                }
            },
            "altText": "Boris Johnson",
            "caption": "Boris Johnson resigns as PM",
            "transformations": null
        }
    }
```

#### Management API: Cropped CMS Image

```json
    {
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "asset": {
                "sys": {
                    "id": "e57979ef-2b86-45e3-8d37-1a744ba2ce7a"
                }
            },
            "altText": "Boris Johnson",
            "caption": "Boris Johnson resigns as PM",
            "transformations": {
                "size": {
                    "width": 1266,
                    "height": 844
                },
                "crop": {
                    "width": 1141,
                    "height": 765,
                    "x": 73,
                    "y": 39
                }
            }
        }
    }
```

#### Delivery API: External image

```json

    {
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "url": "http://www.bbc.co.uk/images/boris_johnson.jpg",
            "altText": "Boris Johnson",
            "caption": "Boris Johnson resigns as PM"
        }
    }
```

#### Delivery API: CMS image

```json
    {
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "url": "/images/boris_johnson.xe0fe632b.jpg",
            "altText": "Boris Johnson",
            "transformations": null,
            "caption": "Boris Johnson resigns as PM",
            "asset": {
                "entryTitle": "boris_johnson",
                "entryDescription": null,
                "sys": {
                    "id": "e57979ef-2b86-45e3-8d37-1a744ba2ce7a",
                    "language": "en-GB",
                    "contentTypeId": "image",
                    "dataFormat": "asset",
                    "uri": "/images/boris_johnson.xe0fe632b.jpg"
                }
            }
        }
    }
```

#### Delivery API: Cropped CMS Image

```json
{
        "type": "_image",
        "id": "gOZ4Mg", // Hashed GUID
        "value": {
            "url": "/images/boris_johnson.xe0fe632b.jpg?w=1266&h=844&crop=1141,765,73,39",
            "altText": "Boris Johnson",
            "transformations": "w=1266&h=844&crop=1141,765,73,39",
            "caption": "Boris Johnson resigns as PM",
            "asset": {
                "entryTitle": "boris_johnson",
                "entryDescription": null,
                "sys": {
                    "id": "e57979ef-2b86-45e3-8d37-1a744ba2ce7a",
                    "language": "en-GB",
                    "contentTypeId": "image",
                    "dataFormat": "asset",
                    "uri": "/images/boris_johnson.xe0fe632b.jpg?w=1266&h=844&crop=1141,765,73,39"
                }
            }
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
  "id": "gOZ4Mg", // Hashed GUID
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
  "id": "gOZ4Mg", // Hashed GUID
  "value": {
    THIS WOULD BE THE COMPONENT IN CONTENSIS TODAY
  },
  "properties": {
    "componentId": "address"
  }
}
```
