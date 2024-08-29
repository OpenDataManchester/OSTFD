---
title: Core Schema
description: The Core schema section of OSTFD contains the main structure of the standard.
---

# Core Schema

The core schemas in OSTFD serve as the functional backbone, streamlining the flow of data from the foundational material to the products sent out in a load. OSTFD deliberately emphasises essential elements to facilitate seamless data exchange across the supply chain. Whenever feasible fields are kept optional ensuring flexibility. Only fields necessary for efficient data exchange and compliance with current regulations are mandatory.

## The schemas

There are six core schemas that are the foundations of OSTFD.

<div class="grid cards" markdown>

-   __Base Materials__

    ---

    Contains information regarding the materials at the very start of the process of creating packaging.

    [:octicons-arrow-right-24: Base materials](./base-materials.md)

-   __Materials__

    ---

    Contains information about how base materials are combined to create more complex materials.

    [:octicons-arrow-right-24: Materials](./materials.md)

-   __Components__

    ---

    Contains the information about how materials are formed into indivudal components. This schema is where a textile and fashion item starts taking form.

    [:octicons-arrow-right-24: Components](./components.md)

-   __Fashion and Textile Products__

    ---

    Contains the information on how components are combined together to create a saleable fashiob and textile product. This schema is the product is fulfilling its intended role.

    [:octicons-arrow-right-24: Fashion and Textile Products](./fashion-and-textile-products.md)

-   __Multipacks (optional)__

    ---

    Contains the information used to sell multipacks of products.

    [:octicons-arrow-right-24: Multipacks](./multipacks.md)

-   __Loads__

    ---

    Contains the information regarding transporting product(s) to a destination.

    [:octicons-arrow-right-24: Loads](./loads.md)


</div>

## The flow
As mentioned OSTFD has been designed to allow information to flow from base materials all the way through to a load. Below you can see how these are connected.
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
    subgraph products[Fashiob and Textile Products]
        cp_example[product]
    end
    subgraph multipacks[Multipacks]
        mp_example[multipack]
    end
    subgraph loads[Loads]
        lo_example[load]
    end
    bm_example --> ma_example
    ma_example --> co_example
    co_example --> cp_example
    cp_example --> lo_example
    cp_example -.-> mp_example
    mp_example -.-> lo_example
```
Each schema (excluding base material) is linked and has a defined relationship with the schema to it's left. This join is important to faciliate the data exchange and to maintain the structure of the data.

## Diagram

``` mermaid
erDiagram
  BASE_MATERIALS }o--o{ MATERIALS : material_constituents
  MATERIALS }o--o{ COMPONENTS : component_constituents
  COMPONENTS }o--o{ PRODUCTS : product_constituents
  PRODUCTS }o..o{ MULTIPACK : multipack_constituents
  COMPONENTS }o..o{ MULTIPACK : multipack_constituents
  PRODUCTS }o..o{ LOADS : load_constituents
  MULTIPACK }o..o{ LOADS : load_constituents
  COMPONENTS }o..o{ LOADS : load_constituents
```

The diagram above shows how the six core schemas interact with each other including their [relationship lists](../relationship-lists/index.md) as these additional entities allow for additional functionality within OSTFD.

The following pages detail the information in each of the schemas, and further show how the core schema work with both the controlled lists and the relationship lists.

