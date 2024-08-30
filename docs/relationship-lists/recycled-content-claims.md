---
title: Recycled Content Claims
description: The recycled content claims relationship list.
---

# Recycled Content Claims

The recycled content claims relationship list identifies the document that details the recycled content claim. This is only used in [components](../schema/components.md).

## Data
|Column|<div style="width:90px">Status</div>|Format|Notes|
|:-|:-|:-|:-|
|identifier|`mandatory`|UUID|A globally unique identifier. See [identifiers](../identifiers/index.md) section for information on how to construct this identifier|
|evidenceType|`mandatory`|String|What type of document provides the information regarding the claim? The entry should be the [recycled content evidence type](../controlled-lists/recycled-content-evidence-types.md) identifier.|
|evidenceReference|`optional`|String|An accompanying reference number associated with the recycled content evidence type for the component.|
|issueDate|`optional`|Date|The date that the recycled content evidence was issued. Use the format `yyyy-mm-dd` adhering to the [ISO 8601 dateTime standard](https://www.iso.org/iso-8601-date-and-time-format.html).|

## Diagram

``` mermaid
erDiagram

  COMPONENTS }o..o{ RECYCLED_CONTENT_CLAIMS : within
  RECYCLED_CONTENT_CLAIMS {
    identifier UUID "*"
    evidenceType String "*"
    evidenceReference String
    issueDate Date
  }
  RECYCLED_CONTENT_CLAIMS }o--o{ CONTROLLED_LISTS : attributes
  CONTROLLED_LISTS {
    recycledContentEvidenceTypes mandatory
  }
```