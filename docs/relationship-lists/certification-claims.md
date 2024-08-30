---
title: Certification Claims
description: The certification claims relationship list.
---

# Certification Claims

The Certification Claims relationship list identifies the certificates that can be assigned to various tables. This is used in the following schemas:

* [Base Materials](../schema/base-materials.md)
* [Materials](../schema/materials.md)
* [Components](../schema/components.md)
* [Fashion and Textile Products](../schema/fashion-and-textile-products.md)

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|source|`mandatory`|String|What source provided the certificate? The entry should be the [Certification Sources Controlled List](../controlled-lists/certification-sources.md) identifier.|
|issueDate|`optional`|Date|The date that the certificate was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o..o{ CERTIFICATION_CLAIMS : within
  MATERIALS }o..o{ CERTIFICATION_CLAIMS : within
  COMPONENTS}o..o{ CERTIFICATION_CLAIMS : within
  PRODUCTS }o..o{ CERTIFICATION_CLAIMS : within
  CERTIFICATION_CLAIMS {
    identifier UUID "*"
    source String "*"
    issueDate Date
  }
  CERTIFICATION_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    certificationSources mandatory 
  }
```