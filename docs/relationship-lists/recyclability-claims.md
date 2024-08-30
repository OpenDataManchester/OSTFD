---
title: Recyclability Claims
description: The recyclability claims relationship list.
---

# Recyclability Claims

The recyclability claims relationship list identifies organisations and schemes that provide the recyclability claims. This is used in the following schemas:

* [Components](../schema/components.md)
* [Fashion and Textile Products](../schema/fashion-and-textile-products.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|source|`mandatory`|String|What source provided the certificate? The entry should be the [recyclability source controlled list](../controlled-lists/recyclability-sources.md) identifier.|
|issueDate|`optional`|Date|The date that the certificate was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ RECYCLABILITY_CLAIMS : within
  PRODUCTS }o..o{ RECYCLABILITY_CLAIMS : within
  RECYCLABILITY_CLAIMS {
    identifier UUID "*"
    source String "*"
    issueDate Date
  }
  RECYCLABILITY_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    recyclabilitySources mandatory 
  }
```
