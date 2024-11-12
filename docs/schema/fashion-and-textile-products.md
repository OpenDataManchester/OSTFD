---
title: Fashion and Textile Products
description: Fashion and textile products are the finished product within OSTFD.
# status: updated
---

# Fashion and Textile Products

The fashion and textile products schema contains information regarding the products that are used to create loads. These maybe created from:

 - a single component 
 - a combination of components
 - other fashion and textile products
 - a combination of components and products

## Table
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|name|`optional`|String|The name of this garment.|
|description|`optional`|String|A brief description of this garment.|
|externalIdentifiers|`optional`|Dictionary|A dictionary of identifiers that is used to identify the garment in other data standards, software systems or protocols. For example: manufacturer's own primary key, bar codes or global trade item number (gtin). To provide external identifiers follow this format. `{'externalIdentifierName1': 'identifier1', 'externalIdentifierName2': 'identifier2'}`. The entries could be drawn from the [External Identifiers Controlled List](../controlled-lists/external-identifiers.md).|
|imageURLs|`optional`|List|URL(s) that links to a picture of the garment. Please see the guidelines below on how to capture the image and name the URL.|
|constituentIdentifiers|`mandatory`|List|The information regarding the consituents that are combined to create this garment. The entries should be from the [Garment Constituents Relationship List](../constituent-lists/product-constituents.md) identifier.|
|endOfLifeRoutes|`optional`|List|The information regarding this garment's proposed end of life routes. The entries should be the [product end of life routes](../relationship-lists/product-end-of-life-routes.md) identifiers.|
|recyclability|`optional`|Boolean|Is the garment recyclable (as determined by a reputable source)? Answer as: `TRUE` for yes and `FALSE` for no.|
|recyclabilityClaims|`optional`|List|The information regarding this recyclability claims. The entries should be the [recyclability claims relationship list](../relationship-lists/recyclability-claims.md) identifiers.|
measurements :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`mandatory`|List|The information regarding the measurements of the garment. The entries should be from the [Measurements Relationship List](../relationship-lists/measurements.md).|
|partOfMultipack|`mandatory`|Boolean|Is the garment part of a multipack? Answer as: `TRUE` for yes and `FALSE` for no.|
|certification|`optional`|Boolean|Does the garment have a certificate (e.g. FSC, REACH, FSA etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|certificationClaims|`optional`|List|The information regarding the certifications. The entries should be the [certification claims relationship list](../relationship-lists/certification-claims.md) identifiers.|
|careLabel :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|Boolean|Does the garment have a care label (e.g. GINETEX, ASTM D5489, ISO 20471 etc.)? Answer as: `TRUE` for yes and `FALSE` for no.|
|careLabelClaims :fontawesome-solid-square-plus:{ title="Added to this version" .addition }|`optional`|List|The information regarding the care labels. The entries should be the [care label claims relationship list](../relationship-lists/care-label-claims.md) identifiers.|
|manufacturers|`optional`|List|The information regarding the manufacturer(s). The entries should be the [Organisations Relationship List](../relationship-lists/organisations.md) identifiers.|
|manufacturedCountry|`optional`|String|The country the component was manufactured in. Use the country numeric [ISO codes](https://www.iso.org/obp/ui/#search){target=_blank} as described in the [ISO 3166 international standard](https://www.iso.org/iso-3166-country-codes.html){target=_blank}.|
|updateDate|`mandatory`|Date|The date that the garment was provided/last updated. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|releaseDate|`optional`|Date|The date that the garment will be available to use. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|
|discontinueDate|`optional`|Date|The date that the garment was discontinued, meaning it was no longer available for purchase. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram
COMPONENTS }o--o{ PRODUCTS : complete_packaging_constituents
  PRODUCTS {
    identifier UUID "*"
    name String
    description String
    externalIdentifiers Dictionary
    imageURLs List
    constituentIdentifiers List "*"
    endOfLifeRoutes List
    recyclability Boolean
    recyclabilityClaims List
    measurements List "*"
    servingCapacity Integer
    servingCapacityDate Date
    partOfMultipack Boolean "*"
    certification Boolean
    certificationClaims List
    careLabel Boolean
    careLabelClaims List
    manufacturers List
    manufacturedCountry String
    updateDate Date "*"
    releaseDate Date
    discontinueDate Date
  }
  PRODUCTS }O..O{ RELATIONSHIP_LISTS : attributes
  PRODUCTS }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  PRODUCTS }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
    RELATIONSHIP_LISTS {
      measurements mandatory
      productEndOfLifeRoutes mandatory
      recyclabilityClaims optional
      certificationClaims optional
      careLabelClaims optional
      organisations optional
    }
```

## Guide for garments images
As with providing measurements, please first find the default front of the garments. The image capturing process and naming convention is similar to [GS1](https://www.gs1.org/standards/gs1-product-image-specification-standard/current-standard#1-Introduction){target=_blank}. 
