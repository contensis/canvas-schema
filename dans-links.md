
## Hyperlink to a url

```html
A link to the <a href="http://www.bbc.co.uk">BBC</a>
```

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "A link to the "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "BBC",
            "properties": {
                "uri": "http://www.bbc.co.uk"                
            }
        }
    ]
}
```

## Hyperlink to an entry

```html
This is my favourite cheese <a href="/entries?id=0000-0000-0000-1234">Cheddar</a>
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234"
                    }
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234",
                        "language": "en-GB"
                    },
                    "entryTitle": "Cheddar",
                    "entryDescription": "Put it on toast"
                },
                "uri": "/en-GB/cheeses/cheddar"
            }
        }
    ]
}
```

## Hyperlink to an entry variation

```html
This is my favourite fromage <a href="/entries?id=0000-0000-0000-1234&language=fr">Le Cheddar</a>
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite fromage "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Le Cheddar",
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234",
                        "language": "fr-FR"
                    }
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite fromage "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Le Cheddar",
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234",
                        "language": "fr-FR"
                    },
                    "entryTitle": "Le Cheddar",
                    "entryDescription": "Dans le pain"
                },
                "uri": "/fr-FR/fromages/le-cheddar"
            }
        }
    ]
}
```

## Hyperlink to a node

```html
This is my favourite cheese <a href="/nodes?id=0000-0000-0000-1234">Cheddar</a>
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                "node": {
                    "id": "0000-0000-0000-1234"                    
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                // should this have data for the specific language
                "node": {
                    "id": "0000-0000-0000-1234",
                    "language": "en-GB",
                    "displayName": "Cheddar",
                    "slug": "cheddar",
                    "entry: {...}
                },
                "uri": "/en-GB/cheeses/cheddar"
            }
        }
    ]
}
```


## Hyperlink to a node variation

```html
This is my favourite fromage <a href="/nodes?id=0000-0000-0000-1234&language=fr-FR">Le Cheddar</a>
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite fromage "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Le Cheddar",
            "properties": {
                "node": {
                    "id": "0000-0000-0000-1234",
                    "language": "fr-FR"
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                // should this have data for the specific language
                "node": {
                    "id": "0000-0000-0000-1234",
                    "language": "fr-FR",
                    "displayName": "le Cheddar",
                    "slug": "le-cheddar"
                },
                "uri": "/fr-FR/fromages/le-cheddar"
            }
        }
    ]
}
```

## Hyperlink to an entry with fragments

```html
This is my favourite cheese <a href="/entries?id=0000-0000-0000-1234"><strong>Cheddar</strong> <em>I love it</em></a>
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": [
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg4",
                    "value": "Cheddar",
                    "properties": {
                        "decorators": [
                            "strong"
                        ]
                    }
                },
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg5",
                    "value": " "
                },
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg6",
                    "value": "I love it",
                    "properties": {
                        "decorators": [
                            "emphasis"
                        ]
                    }
                }
            ],
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234"
                    }
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "This is my favourite cheese "
        },
        {
            "type": "_link",
            "id": "gOZ4Mg3",
            "value": [
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg4",
                    "value": "Cheddar",
                    "properties": {
                        "decorators": [
                            "strong"
                        ]
                    }
                },
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg5",
                    "value": " "
                },
                {
                    "type": "_fragment",
                    "id": "gOZ4Mg6",
                    "value": "I love it",
                    "properties": {
                        "decorators": [
                            "emphasis"
                        ]
                    }
                }
            ],
            "properties": {
                "entry": {
                    "sys": {
                        "id": "0000-0000-0000-1234",
                        "language": "en-GB"
                    },
                    "entryTitle": "Cheddar",
                    "entryDescription": "Put it on toast"
                },
                "uri": "/en-GB/cheeses/cheddar"
            }
        }
    ]
}
```

## Inline entry

```html
The CEO is {Person: Richard Saunders}
```

### Management JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "The CEO is "
        },
        {
            "type": "_inlineEntry",
            "id": "gOZ4Mg3",
            "value": {
                "sys": {
                    "id": "0000-0000-0000-1234"
                }
            }
        }
    ]
}
```

### Delivery JSON

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_fragment",
            "id": "gOZ4Mg2",
            "value": "The CEO is "
        },
        {
            "type": "_inlineEntry",
            "id": "gOZ4Mg3",
            "value": {
                "sys": {
                    "id": "0000-0000-0000-1234"
                },
                "entryTitle": "Richard Saunders",
                "entryDescription": "Richard is the founder and CEO of Zengenti",
                "entryThumbnail": null
            }
        }
    ]
}
```

## Hyperlink and anchor

```html
<a href="#gOZ4Mg2">Skip to main content</a> <a id="gOZ4Mg3"></a> Main content is here
```

```json
{
    "type": "_paragraph",
    "id": "gOZ4Mg1",
    "value": [
        {
            "type": "_link",
            "id": "gOZ4Mg2",
            "value": "Skip to main content",
            "properties": {
                "anchor": "gOZ4Mg3"                
            }
        },
        {
            "type": "_anchor",
            "id": "gOZ4Mg3",
            "value": "",
            "properties": {
                "name": "Main content" // this is so it can be easily identified in the UI
            }
        },
        {
            "type": "_fragment",
            "id": "gOZ4Mg4",
            "value": " Main content is here"
        }
    ]
}
```
