# Dataset Statistics

## 1. Overview

The Bond Graph dataset contains **3,621 graph samples** representing physical systems from five domains:

- Electrical
- Mechanical
- Electromechanical
- Thermal
- Hydraulic

The dataset is designed for research on graph-based learning, Bond Graph component recognition, structural analysis, and physical-system domain classification.

## 2. Dataset Construction and Augmentation

The dataset was constructed from an original collection of annotated Bond Graphs.

A **3× data augmentation strategy** was applied to expand the dataset. The original graphs were retained, and augmented versions were generated to increase the number of available graph samples.

The augmentation process aims to increase dataset diversity while preserving the graph representation and the associated domain labels.

The resulting dataset contains **3,621 graph samples**.

## 3. Domain Distribution

The dataset includes five physical domains. The domain labels are encoded as follows:

| Label | Physical Domain |
|---|---|
| 0 | Electrical |
| 1 | Mechanical |
| 2 | Electromechanical |
| 3 | Thermal |
| 4 | Hydraulic |

The number of graph samples for each domain is:

| Physical Domain | Number of Graphs |
|---|---:|
| Electrical | 993 |
| Mechanical | 774 |
| Electromechanical | 600 |
| Thermal | 360 |
| Hydraulic | 894 |
| **Total** | **3,621** |

## 4. Graph Representation

Each graph is represented using the following attributes:

| Attribute | Description |
|---|---|
| `x` | Node feature matrix with 13 features per node |
| `edge_index` | Directed connectivity between nodes |
| `edge_attr` | Edge attributes containing one feature per edge |
| `y` | Graph-level domain label |

The dataset is stored in PyTorch Geometric-compatible format.

## 5. Annotation Files

The component and edge annotations are provided separately from the graph dataset.

- Component annotations describe the Bond Graph components present in each annotated diagram.
- Edge annotations describe the connections between components and their associated causality labels.

The annotation files are organized by physical domain under:

- `data/annotations/components/`
- `data/annotations/edges/`

For further details, refer to `annotation_protocol.md`.

## 6. Notes

The reported statistics describe the current version of the released graph dataset.

The dataset may be updated in future versions as annotation checks, validation, and documentation improvements are completed.
