---
title: Care Label Claims
description: The care label claims relationship list.
---

# Care Label Claims

The care label claims relationship list identifies the care labels that can be assigned to various schema. This is used in the following schemas:

* [Components](../schema/components.md)
* [Fashion and Textile Products](../schema/fashion-and-textile-products.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|source|`mandatory`|String|What source provided the care label? The entry should be the [Care Label Sources Controlled List](../controlled-lists/care-label-sources.md) identifier.|
|issueDate|`optional`|Date|The date that the care label was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
  COMPONENTS}o..o{ CARE_LABEL_CLAIMS : within
  PRODUCTS }o..o{ CARE_LABEL_CLAIMS : within
  CARE_LABEL_CLAIMS {
    identifier UUID "*"
    source String "*"
    issueDate Date
  }
  CARE_LABEL_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    careLabelSources mandatory 
  }
```