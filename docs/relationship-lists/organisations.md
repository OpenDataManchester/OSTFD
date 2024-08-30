---
title: Organisations
description: The organisations relationship list.
---

# Organisations

The organisations relationship list identifies the organisations that are involved within the packaging value chain. This is used in the following schemas:

* [Base Materials](../schema/base-materials.md)
* [Materials](../schema/materials.md)
* [Components](../schema/components.md)
* [Fashion and Textile Products](../schema/fashion-and-textile-products.md)
* [Multipacks](../schema/multipacks.md)
* [Loads](../schema/loads.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|String|Unique identifier for organisation using [Org.Id format](https://github.com/OpenDataServices/org-ids/). Where possible, using company numbers as the baseline for unambiguous identification. This allows an internationally unique ID (EG: An identifier of the form GB-COH-XXXXXXXX for a UK-registered company). To lookup the format for a location & organisation type use [org-id.guide](http://org-id.guide/).|
|name|`optional`|String|Name of the organisation.|
|postcode|`optional`|String|Postcode for organisation headquarters.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o..o{ ORGANISATIONS : within
  MATERIALS }o..o{ ORGANISATIONS : within
  COMPONENTS }o..o{ ORGANISATIONS : within
  PRODUCTS }o..o{ ORGANISATIONS : within
  MULTIPACK }o..o{ ORGANISATIONS : within
  LOAD }o..o{ ORGANISATIONS : within
  ORGANISATIONS {
    identifier String "*"
    name String
    postcode String
  }
```

## Example

=== "JSON"

    ``` json linenums="1"
    --The organisation information for Open Data Manchester.
    {
      "identifier": "GB-COH-10906273",
      "name": "OPEN DATA MANCHESTER CIC",
      "postcode": "M21 9NU"
    }
    ```