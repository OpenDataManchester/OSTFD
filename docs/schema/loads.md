---
title: Loads
description: The loads contains items what are delivered to a location within OSTFD.
# status: updated
---

# Loads

All the complete packaging from different levels (primary, secondary, transit etc.), including multipacks, put together to send to the final destination. Each row corresponds a unique complete packaging (or multipack) item sent to a specific location during a specific time period.

Note that all core entities can be incorporated into loads. This is to faciliate the interface between one organisastion's product is another organisation's packaging item.

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this load.|
|description|`optional`|String|A brief description of this load.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that is used to identify the load in other data standards, software systems or protocols. For example: manufacturer's own primary key, bar codes or global trade item number (gtin). To provide external identifiers follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|constituentsIdentifiers|`mandatory`|List|The unique identifier of the created load. There must be an equivalent identifier found in the [`Load Constituents`](../constituent-lists/load-constituents.md).|
|measurements :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|List|The information regarding the measurements of the load. The entries should be from the [Measurements Relationship List](../relationship-lists/measurements.md).|
|startDate|`optional`|Date|The date that the load began for the destination. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|endDate|`optional`|Date|The date that the load ended at the destination. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|destinationAddressName|`optional`|String|The name of the load destination address.|
|destinationAddressStreet|`optional`|String|The street address of this load destination.|
|destinationAddressCountry|`optional`|String|The country of this load destination.|
|destinationPostalCode|`optional`|String|The postal code of this load destination.|
|timesSent|`optional`|Integer|The number of times this load was sent to the destination during the specified time period.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../relationship-lists/organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the load was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o..o{ LOADS : load_constituents
MULTIPACK }o..o{ LOADS : load_constituents
COMPONENTS }o..o{ MULTIPACK : multipack_constituents
PRODUCTS }o..o{ MULTIPACK : multipack_constituents
PRODUCTS }o..o{ LOADS : load_constituents
COMPONENTS }o..o{ PRODUCTS : complete_packaging_constituents
  LOADS {
    identifier UUID "*"
    name String
    description String
    externalIdentifier Dictionary
    constituentsIdentifiers List "*"
    measurements List
    startDate Date
    endDate Date
    destinationAddressName String
    destinationAddressStreet String
    destinationAddressCountry String
    destinationPostalCode String
    timesSent Integer
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
  }
  LOADS }o--o{ RELATIONSHIP_LISTS : attributes
  RELATIONSHIP_LISTS {
      organisations optional
      measurements optional
    }
```
