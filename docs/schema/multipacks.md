---
title: Multipacks
description: Multipacks contain multiple identical garments within OSTFD.
# status: updated
---

# Multipacks

The multipacks schema contains information regarding the multipacks that are used to create loads. These are created from a number of either identical or different garments from the fashion and textile products schema.

!!! note "Optional"

    The multipack portion is optional (only applies to multipacks). If the garmemt or component is *not* in a multipack, all of the fields below are optional.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this multipack.|
|description|`optional`|String|A brief description of this multipack.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that is used to identify the mutlipack in other data standards, software systems or protocols. For example: manufacturer's own primary key, bar codes or global trade item number (gtin). To provide external identifiers follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|constituentsIdentifiers|`mandatory`|List|The information regarding the consituents that are combined to create this multipack. The entries should be from the [Multipack Constituents Relationship List](../constituent-lists/multipack-constituents.md) identifier.|
|tier|`optional`|Integer|The tier associated with the multipack. The inner most tier denoted as 1, and the outermost tier is the biggest number.|
|measurements :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|List|The information regarding the measurements of the multipack. The entries should be from the [Measurements Relationship List](../relationship-lists/measurements.md).|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../relationship-lists/organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the multipack was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the multipack will be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|discontinueDate|`optional`|Date|The date that the multipack was discontinued, meaning it was no longer available for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o..o{ MULTIPACK : multipack_constituents
COMPONENTS }o..o{ PRODUCTS : products_constituents
PRODUCTS }o..o{ MULTIPACK : multipack_constituents
  MULTIPACK {
    identifier UUID "*"
    name String
    description String
    externalIdentifiers Dictionary
    constituentsIdentifiers List "*"
    tier String
    measurements List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  MULTIPACK }o--o{ RELATIONSHIP_LISTS : attributes
  PRODUCTS }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o--o{ LOADS : load_constituents
      RELATIONSHIP_LISTS {
        organisations optional
        measurements optional
    }
```