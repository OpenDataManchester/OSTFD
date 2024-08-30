---
title: Product End of Life Routes
description: The product end of life routes relationship list.
---

# Product End of Life Routes

The product end of life routes relationship list identifies the purposed and intended destination and process of this product once it has completed its role. This is only used in [textile and fashion products](../schema/fashion-and-textile-products.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifer|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|productEndOfLifeRoute|`mandatory`|String|What is the intended end of life route for this product. The entry should be the [end of life route controlled list](../controlled-lists/end-of-life-routes.md) identifier. To be filled in when the product has an intended end of life route AS a product, otherwise only fill out at component level.|
|orderOfPrecedence|`optional`|Integer|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|disruptors|`optional`|List|What challenges this end of life route for this product. The entry should be the [product end of life route disruptors controlled list](../controlled-lists/product-disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  PRODUCTS }o..o{ PRODUCT_END_OF_LIFE_ROUTES : within
  PRODUCT_END_OF_LIFE_ROUTES {
    identifier UUID "*"
    endOfLifeRoute String "*"
    orderOfPrecedence Integer
    completePackagingDistruptors List
  }
  PRODUCT_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    endOfLifeRoutes mandatory
    productDistruptors mandatory
  }
```

