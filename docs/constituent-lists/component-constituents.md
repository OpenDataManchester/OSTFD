---
title: Component Constituents
description: The component constituents list.
---

# Component Constituents

The component constituents list identifies the materials and components that are combined to create components. This is only used in [components](../schema/components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|combinationIdentifier|`mandatory`|UUID|The unique identifier of the materials and components that this component is made of. There must be an equivalent record in the `Materials` OR `Components` data.|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ COMPONENT_CONSTITUENTS : within
  COMPONENT_CONSTITUENTS {
    identifier UUID "*"
    componentCombinationIdentifier UUID "*"
  }
  COMPONENT_CONSTITUENTS }o--o{ MATERIALS : attributes
  COMPONENT_CONSTITUENTS }o--o{ COMPONENTS : attributes
```