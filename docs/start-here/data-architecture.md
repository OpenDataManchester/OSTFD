---
title: Data Architecture
description: The current data architecture of the OSTFD open data standard for the apparel value chain.
---

# Data Architecture

Within the OSTFD standard there are two features that are equally important and the use of these features is a key component to correctly implamenting the standard.

The first is our core schemas. These are at functional backbone of the standard. This is where the majority of the data is held. These are shown below as the rectangles.

The second is our relationships. These define the relationships between these core schemas. These are shown below as the lines.

``` mermaid
erDiagram
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS }o--o{ COMPONENTS : component_constituents
  COMPONENTS }o--o{ GARMENTS : garment_constituents
  GARMENTS }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  GARMENTS }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
```
