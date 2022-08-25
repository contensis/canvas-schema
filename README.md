# Contensis canvas specification

**Version**: Working Draft

***

## Description

## Terminology

| Term | Definition |
|:--|:--|
| _types | String |
| Fragments | Array |
| Decorators | Array |
| Properties | Additional attributes of a `_type` that describe or enhance the primary value of the type. e.g. A title enhances primary message of a `_panel`, a source enhances a `_quote`. |
| id/uuid | string, representing the unique value or key of single piece of content within a Canvas. |

## Supported types

### _type rules

- When the `value` of a `_type` can be styled with decorator, then any additional attributes of that type are defined as properties.
- When the `value` of a `_type` that supports decorators is not styled, then the value is stored as a simple string. This makes it easier to read and reduces the storage required.

### Standard types

| Type | Status |
|:--|:--|
| [_paragraph](standard-types.md#_paragraph)| :white_check_mark: Approved |
| [_heading](standard-types.md#_heading)| :white_check_mark: Approved |
| [_list](standard-types.md#_list)| :white_check_mark: Approved |
| [_code](standard-types.md#_code)| :white_check_mark: Approved |
| [_table](standard-types.md#_table)| :white_check_mark: Approved |
| [_quote](standard-types.md#_quote)| :white_check_mark: Approved |
| [_divider](standard-types.md#_divider)| :white_check_mark: Approved |
| [_panel](standard-types.md#_panel)| :white_check_mark: Approved |
| [_embed](standard-types.md#_embed)| :white_check_mark: Approved |
| [_bookmark](standard-types.md#_bookmark)| :white_check_mark: Approved |

### Contensis types

| Type | Status |
|:--|:--|
| [_image](contensis-types.md#_image)| :white_check_mark: Approved |
| [_imageArray](contensis-types.md#_imageArray)| :warning: Needs discussion |
| [_component](contensis-types.md#_component)| :warning: Needs discussion |

***

## Decorators

Decorators are applied to `_fragment`s to describe and define the text to give it richness. Decorators are defined as arrays within the properties object of a `_fragment`. Decorators can be paired with their own property object to extend their definition. As seen in the link decorator.

| Type | Status |
|:--|:--|
| [strong](decorators.md#strong)| :white_check_mark: Approved |
| [emphasis](decorators.md#emphasis)| :white_check_mark: Approved |
| [strikethrough](decorators.md#strikethrough)| :white_check_mark: Approved |
| [subscript](decorators.md#subscript)| :white_check_mark: Approved |
| [superscript](decorators.md#superscript)| :white_check_mark: Approved |
| [mark](decorators.md#mark)| :white_check_mark: Approved |
| [code](decorators.md#code)| :white_check_mark: Approved |
| [keyboard](decorators.md#keyboard)| :white_check_mark: Approved |
| [variable](decorators.md#variable)| :white_check_mark: Approved |
| [insert](decorators.md#insert)| :white_check_mark: Approved |
| [delete](decorators.md#delete)| :white_check_mark: Approved |
| [link](decorators.md#link)| :warning: Needs discussion |
| [anchor](decorators.md#anchor)| :warning: Needs discussion |
