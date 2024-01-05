---
title: Data Schema
description: The current data schema of the Open 3P open data standard for the packaging value chain.
---

# Data Schema
``` mermaid
erDiagram
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS }o--o{ COMPONENTS : component_constituents
  COMPONENTS }o--o{ COMPLETE_PACKAGING : complete_packaging_constituents
  COMPLETE_PACKAGING }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  BASE_MATERIALS }o..o{ LOADS : load_constituents
  MATERIALS }o..o{ LOADS : load_constituents
  COMPLETE_PACKAGING }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
```