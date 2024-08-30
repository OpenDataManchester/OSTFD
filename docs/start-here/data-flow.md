---
title: Data Flow
description: The intented flow of data through the packaging value chain using Open 3P.
---

# Data Flow
Here, we show examples of how data could flow using the open standard. This tells the story of how wine bottles are created with a packaging manufacturer, how that packaging manufacturer sends their packaging to a packer/filler and then how that packer/filler will put packaging together, filled with a product and then send them to a retailer. The eight flow diagrams below compliment each other to build a complete picture.

!!! note "Shared responsiblity"

    When viewing the flows below be aware that no single individual and/or organisation is responsible for the entire data capture.
    It is the intent of Open 3P that experts in their part of the value chain are repsonsible for it's adherence to the data. 

## The flow
Open 3P has been designed to allow information to flow from base materials all the way through to a load. Below you can see how these are connected.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_example[base material]
    end
    subgraph materials[Materials]
        ma_example[material]
    end
    subgraph components[Components]
        co_example[component]
    end
    subgraph completePackages[Complete Packages]
        cp_example[complete package]
    end
    subgraph loads[Loads]
        lo_example[load]
    end
    bm_example --> ma_example
    ma_example --> co_example
    co_example --> cp_example
    cp_example --> lo_example
```
