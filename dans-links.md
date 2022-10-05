
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
            "type": "_hyperlink",
            "id": "gOZ4Mg3",
            "value": "BBC",
            "properties": {
                "url": "http://www.bbc.co.uk"                
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
            "type": "_hyperlink",
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
            "type": "_hyperlink",
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
                "url": "/en-GB/cheeses/cheddar"
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
            "type": "_hyperlink",
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
            "type": "_hyperlink",
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
                "url": "/fr-FR/fromages/le-cheddar"
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
            "type": "_hyperlink",
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
            "type": "_hyperlink",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                "node": {
                    "id": "0000-0000-0000-1234",
                    "language": "en-GB",
                    "displayName": "Cheddar",
                    "slug": "cheddar"
                },
                "url": "/en-GB/cheeses/cheddar"
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
            "type": "_hyperlink",
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
            "type": "_hyperlink",
            "id": "gOZ4Mg3",
            "value": "Cheddar",
            "properties": {
                "node": {
                    "id": "0000-0000-0000-1234",
                    "language": "fr-FR",
                    "displayName": "le Cheddar",
                    "slug": "le-cheddar"
                },
                "url": "/fr-FR/fromages/le-cheddar"
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
            "type": "_hyperlink",
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
            "type": "_hyperlink",
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
                "url": "/en-GB/cheeses/cheddar"
            }
        }
    ]
}
```
