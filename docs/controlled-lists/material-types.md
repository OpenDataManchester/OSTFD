---
title: Material Type
description: The material type controlled list for base materials.
---

# Material Type

The Material Type controlled list identifies the type of the [base material](../schema/base-materials.md).

**Controlled lists are maintained by the SCB, if there are values that you believe need to be added then [contact us](https://www.open3p.org/contact/) and we can add new values to the lists.**

## Data
|<div style="width:150px">identifier</div>|category|detailed|
|:-|:-|:-|
|bm-material-type-0001|Fossil based|Materials derived from fossil sources, which include the remains of ancient plants and animals. This category encompasses substances like oil-based products, gas-based materials, and coal-based resources.|
|bm-material-type-0002|Animal based|Materials obtained from animal sources. This category includes a wide range of materials such as leather, wool, silk, and other products derived from animals.|
|bm-material-type-0003|Plant based|Materials sourced from plants and plant-derived substances. This category covers a diverse array of materials. Including: wood, cotton, hemp, fungi and other plant-based fibres.|
|bm-material-type-0004|Mineral based|Materials obtained from non-living sources, specifically minerals. This category includes a broad range of substances like stones, and other mineral resources.|
|bm-material-type-0005|Metal based|Materials specifically derived from metals. This category includes various metallic elements and alloys.|

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o..o| MATERIAL_TYPE : controlled_list
```