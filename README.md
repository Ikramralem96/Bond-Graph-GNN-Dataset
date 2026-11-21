# Bond-Graph-GNN-Dataset

## 1. Overview

This repository provides a graph-structured dataset of Bond Graph models designed for research on Graph Neural Networks (GNNs), structural learning, component recognition, causality analysis, and physical-system classification.

The dataset contains **3,621 graph samples** covering five physical domains:

- Electrical
- Mechanical
- Electromechanical
- Thermal
- Hydraulic

Each Bond Graph model is represented as a structured graph containing node features, directed connectivity information, edge attributes, and a physical-domain label.

The objective is to provide structured data that supports the development and evaluation of machine learning approaches for Bond Graph analysis.

## 2. Dataset Composition

The dataset contains 3,621 graph samples distributed across five physical domains.

| Label | Physical Domain | Number of Graphs |
|---|---|---:|
| 0 | Electrical | 993 |
| 1 | Mechanical | 774 |
| 2 | Electromechanical | 600 |
| 3 | Thermal | 360 |
| 4 | Hydraulic | 894 |
| **Total** | | **3,621** |

## 3. Graph Representation

Each Bond Graph model is represented as a graph:

\[
G = (X, E, A, y)
\]

where:

- `x`: Node feature matrix representing Bond Graph components using 13-dimensional feature vectors.
- `edge_index`: Directed connectivity information between nodes.
- `edge_attr`: Edge attributes representing causality information.
- `y`: Graph-level label identifying the physical domain.

The dataset is compatible with PyTorch Geometric.

## 4. Dataset File

The main dataset file is:

`all_graphs_Multi_domain.pt`

It contains the graph samples stored as PyTorch Geometric Data objects.

## 5. Loading the Dataset

The dataset can be loaded using PyTorch and PyTorch Geometric:

```python
import torch
from torch_geometric.data import Data

dataset = torch.load(
    "all_graphs_Multi_domain.pt",
    map_location="cpu",
    weights_only=False
)

print("Number of graphs:", len(dataset))

# Inspect the first graph
graph = dataset[0]

print("Node features:", graph.x.shape)
print("Edge index:", graph.edge_index.shape)
print("Edge attributes:", graph.edge_attr.shape)
print("Domain label:", graph.y)
```

**Requirements:**

- Python
- PyTorch
- PyTorch Geometric

## 6. Annotation Files

The dataset is accompanied by separate annotation files covering two aspects of Bond Graph modeling:

**Component annotations**

These files contain component-level annotations for the five physical domains.

**Edge annotations**

These files document graph connections and associated causality information.

The annotation files are provided separately from the main PyTorch dataset to facilitate inspection, analysis, and reuse.

## 7. Repository Structure

The repository is organized as follows:

```text
Bond-Graph-GNN-Dataset/
│
├── README.md
├── CITATION.cff
│
├── data/
│   ├── all_graphs_Multi_domain.pt
│   │
│   └── annotations/
│       ├── components/
│       │   ├── components_labels_Electrical.csv
│       │   ├── components_labels_Mechanical.csv
│       │   ├── components_labels_Electromechanical.csv
│       │   ├── components_labels_Thermal.csv
│       │   └── components_labels_Hydraulic.csv
│       │
│       └── edges/
│           ├── edges_annotations_Electrical.csv
│           ├── edges_annotations_Mechanical.csv
│           ├── edges_annotations_Electromechanical.csv
│           ├── edges_annotations_Thermal.csv
│           └── edges_annotations_Hydraulic.csv
│
└── documentation/
    ├── graph_format.md
    ├── annotation_protocol.md
    └── dataset_statistics.md
```

## 8. Intended Applications

This dataset is intended to support research on:

- Bond Graph component recognition.
- Graph Neural Networks for physical-system modeling.
- Structural learning and graph classification.
- Causality analysis in Bond Graph systems.
- Multi-domain physical-system classification.
- Development of data-driven tools for Bond Graph analysis.

## 9. Source Material and Data Construction

The graph samples were constructed from Bond Graph diagrams collected from scientific and technical sources.

The original source images and publication PDFs are **not included** in this dataset.

The distributed dataset consists of structured graph representations, including node features, graph connectivity, edge attributes, and physical-domain labels.

Component and edge annotations are provided separately to document the annotation structure.

## 10. Citation

If you use this dataset in your research, please cite it as follows:

Ralem, I. (2026). *Bond-Graph-GNN-Dataset* (Version 1.0.0). Zenodo. https://doi.org/10.5281/zenodo.24379981

## 11. License

This dataset is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

You are free to share and adapt the dataset, provided appropriate credit is given to the creator, a link to the license is provided, and any changes are indicated.

Original source images and publication PDFs are not redistributed as part of this dataset.

Copyright © 2026 Ikram Ralem.
