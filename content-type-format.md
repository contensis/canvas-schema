#  Proposed updated Content type format

## Types

The *type* property in validations should match the *type* property in the canvas json schema.

### Limiting to certain types

Only allow headings and lists

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedTypes": {
                "types": [
                    {
                        "type": "_heading"
                    },
                    {
                        "type": "_list"
                    }
                ],
                "message": {
                    "en-GB": "This type is not permitted."
                }
            }
        }
    }
}
```

### Enabling all types

Allow all 

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedTypes": {
                "types": [
                    {
                        "type": "*"
                    }
                ],
                "message": {
                    "en-GB": "This type is not permitted."
                }
            }
        }
    }
}
```

### Configuring certain types

Only allow code and only javascript as a language

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedTypes": {
                "types": [
                    {
                        "type": "_code",
                        "languages": {
                            "languages": [
                                "Javascript"
                            ],
                            "message": {
                                "en-GB": "Only javscript is allowed"
                            }
                        }
                    }
                ],
                "message": {
                    "en-GB": "This type is not permitted."
                }
            }
        }
    }
}
```

### Configuring types when all types are allowed

Allow all types but only javascript as a code language

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedTypes": {
                "types": [
                    {
                        "type": "*"
                    },
                    {
                        "type": "_code",
                        "languages": {
                            "languages": [
                                "Javascript"
                            ],
                            "message": {
                                "en-GB": "Only javscript is allowed"
                            }
                        }
                    }
                ],
                "message": {
                    "en-GB": "This type is not permitted."
                }
            }
        }
    }
}
```

### Specific validations for each type

All the validations for specific type, if absent all will be allowed ie. if no languages are specified for _code then all languages can be used.

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedTypes": {
                "types": [
                    {
                        "type": "_code",
                        "languages": {
                            "languages": [
                                "Javascript"
                            ],
                            "message": {
                                "en-GB": "Only javscript is allowed"
                            }
                        }
                    },
                    {
                        "type": "_component",
                        "components": {
                            "components": [
                                "addressComponent"
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_heading",
                        "levels": {
                            "levels": [
                                2,
                                4
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_link",
                        "linkTypes": {
                            "types": [
                                "anchor",
                                "url",
                                "entry",
                                "node"
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_list",
                        "listTypes": {
                            "types": [
                                "ordered",
                                "unordered"
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_panel",
                        "linkTypes": {
                            "types": [
                                "info",
                                "note",
                                "warning",
                                "success",
                                "error"
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_paragraph",
                        "paragraphTypes": {
                            "types": [
                                "lede"
                            ],
                            "message": {}
                        }
                    }
                ],
                "message": {
                    "en-GB": "This type is not permitted."
                }
            }
        }
    }
}
```

## Decorators

The *decorator* property in validations should match a decorator in the canvas json schema.

### Allowing all decorators
```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedDecorators": {
                "decorators": [
                    {
                        "decorator": "*"
                    }
                ],
                "message": {
                    "en-GB": "This decoartor is not permitted."
                }
            }
        }
    }
}
```

### Allowing only certain decorators

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedDecorators": {
                "decorators": [
                    {
                        "decorator": "emphasis"
                    },
                    {
                        "decorator": "strong"
                    }
                ],
                "message": {
                    "en-GB": "This decorator is not permitted."
                }
            }
        }
    }
}
```

## Allowing generic properties

Some properties are available on all types and decorators, at the moment this only *id*, again no validation means all properties are output

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedProperties": {
                "properties": [
                    {
                        "property": "id"
                    }
                ],
                "message": {
                    "en-GB": "This only the id property is allowed."
                }
            }
        }
    }
}
```

### Turn off all generic properties

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "validations": {
        "canvas": {
            "allowedProperties": {
                "properties": [],
                "message": {
                    "en-GB": "The id property is not allowed."
                }
            }
        }
    }
}
```

## Editor settings

With the exception of *image* I don't think any of these would be turned off, if an action is not specified it is enabled

```json
{
    "id": "canvasField",
    "name": {
        "en-GB": "Canvas Field"
    },
    "dataType": "objectArray",
    "dataFormat": "canvas",
    "editor": {
		"id": "canvas",
		"instructions": {},
		"properties": {
			"uploadPath": "/image-library",
            "actions": {
                "contentEditable": true,
				"customCommand": true,
				"deleteItem": true,
				"duplicate": true,
				"editorPanel": true,
				"order": true,
                "image": ["crop", "upload"]
            }
		}
	}
}
```
