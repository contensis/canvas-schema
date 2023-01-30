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
                            "allowed": [
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
                            "allowed": [
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

All the validations for specific type, if absent all will be allowed ie. if no languages are specified for _code_ then all languages can be used.

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
                            "allowed": [
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
                            "allowed": [
                                "addressComponent"
                            ],
                            "message": {}
                        }
                    },
                    {
			"type": "_fragment",
			"decorators": {
			    "allowed": [
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
		    },
                    {
                        "type": "_heading",
                        "levels": {
                            "allowed": [
                                2,
                                4
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_link",
                        "linkTypes": {
                            "allowed": [
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
                            "allowed": [
                                "ordered",
                                "unordered"
                            ],
                            "message": {}
                        }
                    },
                    {
                        "type": "_panel",
                        "linkTypes": {
                            "allowed": [
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
                            "allowed": [
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
            "allowedTypes": {
                "types": [
                    {
		        "type": "_fragment",
			"decorators": {
			    "allowed": [
			        { "decorator": "*" }
			    ],
			    "message": {
			        "en-GB": "This decorator is not permitted."
			    }
			}
	            }
                ]
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
            "allowedTypes": {
                "types": [
                    {
		        "type": "_fragment",
			"decorators": {
			    "allowed": [
			        { "decorator": "emphasis" },
                                { "decorator": "strong" }
			    ],
			    "message": {
			        "en-GB": "This decorator is not permitted."
			    }
			}
		    }
                ]
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
                "image": [
                    "crop",
                    "upload"
                ]
            }
        }
    }
}
```
