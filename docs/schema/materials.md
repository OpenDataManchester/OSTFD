---
title: Materials
description: Materials are a combination of base materials within OSTFD.
# status: updated
---

# Materials

The materials schema contains information regarding the materials that are used within components. These maybe created from:

 - a single base material 
 - a combination of base materials
 - other materials
 - a combination of base materials and materials

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|The globally unique identifier for the created material unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|name|`mandatory`|String|The name of the material this row relates to. `e.g. felt or demin or polyester` |
|description|`optional`|String|A brief description of this material.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that is used to identify the material in other data standards, software systems or protocols. For example: manufacturer's own primary key, bar codes or global trade item number (gtin). To provide external identifiers follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|constituentIdentifiers|`mandatory`|List|The information regarding the constituents that are combined to create this material. The entries should be from the [Material Constituents List](../constituent-lists/material-constituents.md) identifier.|
|combinationPurpose|`optional`|String|Why is this material being used? Use the identifier of the function that this row relates to. The entry here should be drawn from the [Functions Controlled List](../controlled-lists/functions.md).|
|measurements :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|List|The information regarding the measurements of the material. The entries should be from the [Measurements Relationship List](../relationship-lists/measurements.md).|
|certification|`optional`|Boolean|Does the material have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certification. The entries should be the [Certification Claims Relationship List](../relationship-lists/certification-claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../relationship-lists/organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the material was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the material was first listed for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|
|discontinueDate|`optional`|Date|The date that the material was delisted, meaning it was no longer available for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html){target=_blank}.|

## Diagram

``` mermaid
erDiagram
BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS {
    identifier UUID "*"
    name String "*"
    description String
    externalIdentifiers Dictionary
    materialConstituents List "*"
    combinationPurpose String
    measurements List
    certification Boolean
    certificationClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
  }
  MATERIALS }o..o{ CONTROLLED_LISTS : attributes
  MATERIALS }o--o{ COMPONENTS : component_constituents
  MATERIALS }o..o{ RELATIONSHIP_LISTS : attributes
        CONTROLLED_LISTS {
    functions optional
    }
        RELATIONSHIP_LISTS {
    certificationClaims optional
    organisations optional
    measurements optional
      }
```

## Guide for how to take measurements

### Units

All measurements should be given using the metric system.

- Weight: grams (g)
- Area Density: grams per square metre (gsm) or square metres per kilogram (m^2/kg)

Numbers should be entered with a decimal place. Use the decimal / full stop / period character as a separator. Do not exceed 3 decimal places. When rounding, use convential rounding methods: for 5 and above round up, 4 and below round down. For example: volume = 0.67952 rounded to 0.68. 

**Important**: When converting between systems of measurement, perform the conversion first and then apply the convential rounding. This will give more accuracy and consistency.
