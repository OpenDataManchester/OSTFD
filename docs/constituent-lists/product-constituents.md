---
title: Fashion and Textile Product Constituents
description: The fashion and textile product constituents list.
---

# Fashion and Textile Product Constituents

The fashion and textile product constituents list identifies the components and other products that are combined to create fashion and textile products. This is only used in [fashion and textile products](../schema/fashion-and-textile-products.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|combinationIdentifier|`mandatory`|UUID|The unique identifier of the components and/or fashion and textile products that this fashion and textile product is made of. There must be an equivalent record in the `Components` OR `fashion and textile product` data.|

## Diagram

``` mermaid
erDiagram

  PRODUCTS }o..o{ PRODUCT_CONSTITUENTS : within
  PRODUCT_CONSTITUENTS {
    identifier UUID "*"
    combinationIdentifier UUID "*"
  }
  PRODUCT_CONSTITUENTS }o--o{ COMPONENTS : attributes
  PRODUCT_CONSTITUENTS }o--o{ PRODUCTS : attributes
```