---
title: Multipack Constituents
description: The multipack constituents list.
---

# Multipack Constituents

The multipack constituents list identifies the fashion and textile products and components that are combined to create multipacks. This is only used in [multipacks](../schema/multipacks.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|combinationIdentifier|`mandatory`|UUID|The unique identifier of components and/or complete packaging that this multipack is made of. There must be an equivalent record in the `Components` OR `Complete Packaging` data.|
|identicalQuantity|`mandatory`|Integer|Number of identical units of the component and/or complete package that this multipack is made of.|

## Diagram

``` mermaid
erDiagram

  MULTIPACK }o..o{ MULTIPACK_CONSTITUENTS : within
  MULTIPACK_CONSTITUENTS {
    identifier UUID "*"
    combinationIdentifier UUID "*"
    identicalQuantity integer "*"
  }
  MULTIPACK_CONSTITUENTS }o--o{ PRODUCTS : attributes
  MULTIPACK_CONSTITUENTS }o--o{ COMPONENTS : attributes
```
