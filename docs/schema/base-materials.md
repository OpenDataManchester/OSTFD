---
title: Base Materials
description: Base materials are the building blocks of OSTFD.
# status: updated
---

# Base Materials

The base materials schema contains information regarding the materials at the very start of the process of creating a product. These are then combined together within the materials table to create more complicated materials.

!!! question "Frequently Asked Question"

    Do all fashion and textiles items need to contain a `Base Material`?

    Yes, every fashion and textiles item must include a Base Material. This foundational component serves as the building block for all fashion and textile materials. The level of detail in specifying base material(s) can vary based on requirements. For more in-depth insights, refer to the Data Flow section.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier.|
|name|`mandatory`|String|The name of the base material this row relates to. `e.g. Cotton or Polypropylene or Wool`.|
|description|`optional`|String|A brief description of this base material.|
|type|`optional`|String|What type of base material is this? The entry here should be drawn from the [Material Types Controlled List](../controlled-lists/material-types.md).|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that is used to identify the base material in other data standards, software systems or protocols. For example: manufacturer's own primary key, bar codes or global trade item number (gtin). To provide external identifiers follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|measurements :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|List|The information regarding the measurements of the base material. The entries should be from the [Measurements Relationship List](../relationship-lists/measurements.md).|
|certification|`optional`|Boolean|Does the base material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../relationship-lists/certification-claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../relationship-lists/organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the base material was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the base material was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|
|releaseDate|`optional`|Date|The date that the base material was first listed for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|
|discontinueDate|`optional`|Date|The date that the base material was discontinued, meaning it was no longer available for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS {
    identifier UUID "*"
    name String "*"
    description String
    type String
    externalIdentifiers Dictionary
    measurements List
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  BASE_MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  BASE_MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
  CONTROLLED_LISTS {
    materialType optional
  }
  RELATIONSHIP_LISTS {
    certificationClaims optional
    organisations optional
    measurements optional
  }
```