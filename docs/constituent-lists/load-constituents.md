---
title: Load Constituents
description: The load constituents list.
---

# Load Constituents

The loads constituents list identifies all the fashion and textile products from different levels (primary, secondary, transit etc.) and multipacks that are combined to create loads. This is only used in [load](../schema/loads.md).

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|combinationIdentifier|`mandatory`|UUID|The unique identifier of the items that this component is made of. There must be an equivalent record in the `Components`, `Complete_Packaging` OR `Multipacks` data.|
|name|`optional`|String|The name of this load constituent.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that might be used to identify the load constituents in other systems. For example: manufacturer's own internal identifier, bar codes or global trade item number (gtin). To provide external identifiers please follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|quantityInLoad|`mandatory`|Integer|Number of units for the packaging items found in a load that this row corresponds to.|
|level|`mandatory`|String|The intended use of the component for the packaging. The entry here should be drawn from the [level controlled list](../controlled-lists/levels.md).|

## Diagram

``` mermaid
erDiagram
  COMPONENTS }o..o{ LOAD_CONSTITUENTS : attributes
  PRODUCTS }o..o{ LOAD_CONSTITUENTS : attributes
  MULTIPACKS }o..o{ LOAD_CONSTITUENTS : attributes
  LOAD_CONSTITUENTS {
    loadConstituentsIdentifier UUID "*"
    loadCombinationIdentifier UUID "*"
    name String
    externalIdentifiers Dictionary
    quantityInLoad Integer "*"
    level String "*"
  }
  LOAD_CONSTITUENTS }o--o{ LOAD : within
  LOAD_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    level mandatory
  }
```