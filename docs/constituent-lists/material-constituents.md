---
title: Material Constituents
description: The material constituents list.
---

# Material Constituents

The material constituents list identifies the base materials and other materials that are combined to create materials. This is only used in [materials](../schema/materials.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|combinationIdentifier|`mandatory`|UUID|The unique identifier of the materials that this component is made of. There must be an equivalent record in the `Base_Materials` OR `Materials` data.|
|materialPurpose|`optional`|String|Why is this base material or material being used? Use the identifier of the material purpose that this row relates to. The entry here should be drawn from the [Material Purpose Controlled List](../controlled-lists/material-purposes.md).|
|virginMaterial|`optional`|Decimal|The maximum allowable percent of the material that was newly created for the material.|
|layer|`optional`|Integer|The layer associated with the material. The inner most layer (the layer closest to the product) denoted as 1, and the outermost layer is the biggest number.|
|materialPercentage|`optional`|Decimal|The percentage of the total materials making-up the material. For every unique material, materialPercentage should add to 100%.|

## Diagram

``` mermaid
erDiagram

  MATERIALS }o..o{ MATERIAL_CONSTITUENTS : within
  MATERIAL_CONSTITUENTS {
    materialConstituentsIdentifier UUID "*"
    materialCombinationIdentifier UUID "*"
    materialPurpose String
    virginMaterial Decimal
    layer Integer
    materialPercentage Decimal
  }
  MATERIAL_CONSTITUENTS }o--o{ BASE_MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ MATERIALS : attributes
  MATERIAL_CONSTITUENTS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    materialPurposeControlledList mandatory 
  }
```
