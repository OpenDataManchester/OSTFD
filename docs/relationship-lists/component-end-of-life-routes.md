---
title: Component End of Life Routes
description: The component end of life routes relationship list.
---

# Component End of Life Routes

The component end of life routes relationship list identifies the purposed and intended destination and process of this component once it has completed its role as packaging. This is only used in [components](../schema/components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|endOfLifeRoute|`mandatory`|String|What is the intended end of life route for this component? The entry should be the [end of life route controlled list](../controlled-lists/end-of-life-routes.md) identifier.|
|orderOfPrecedence|`optional`|Integer|The order that end of life routes should be used. The preferred route denoted as 1, and the last best option being the biggest number.|
|componentDisruptors|`optional`|List|What challenges this end of life route for this component has. The entry should be the [component end of life route disruptors controlled list](../controlled-lists/component-disruptors.md) identifier.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ COMPONENT_END_OF_LIFE_ROUTES : within
  COMPONENT_END_OF_LIFE_ROUTES {
    identifier UUID "*"
    route String "*"
    orderOfPrecedence Integer
    componentDistruptors List
  }
  COMPONENT_END_OF_LIFE_ROUTES }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    endOfLifeRoutes mandatory
    componentDistruptors mandatory
  }
```