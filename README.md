# Bond-Graph-GNN-Dataset

## 1. Overview

This repository provides a graph-structured dataset of Bond Graph models for research on Graph Neural Networks (GNNs), structural learning, component recognition, causality analysis, and physical-system classification.

The dataset covers five physical domains:

- Electrical
- Mechanical
- Electromechanical
- Thermal
- Hydraulic

The objective is to provide structured graph data that can support the development and evaluation of machine learning approaches for Bond Graph analysis.

## 2. Dataset Statistics

The dataset contains **3,621 Bond Graph samples** distributed across five physical domains.

| Label | Physical Domain | Number of Graphs |
|---|---|---:|
| 0 | Electrical | 993 |
| 1 | Mechanical | 774 |
| 2 | Electromechanical | 600 |
| 3 | Thermal | 360 |
| 4 | Hydraulic | 894 |
| | **Total** | **3,621** |

The dataset was constructed from an original collection of Bond Graphs and expanded using a **3× data augmentation strategy**.

The five physical domains are encoded using the numerical labels shown in the table above.

The dataset is provided in PyTorch Geometric-compatible graph format.

## 3. Graph Representation

Each Bond Graph is represented as a graph with the following attributes:

| Attribute | Description |
|---|---|
| `x` | Node feature matrix containing 13 features per node |
| `edge_index` | Directed connectivity information between graph nodes |
| `edge_attr` | Edge attributes containing one feature per edge |
| `y` | Graph-level physical-domain class label |

The graph representation preserves the node and edge information required for graph-based learning tasks.

Additional information about the graph structure and data format is available in [`documentation/graph_format.md`](documentation/graph_format.md).

## 4. Dataset File

The main dataset file is:

`data/all_graphs_Multi_domain.pt`

It contains the 3,621 graph samples used for multi-domain Bond Graph research.

## 5. Repository Structure

The repository is organized as follows:

```text
Bond-Graph-GNN-Dataset/
│
├── README.md
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

## 6. Loading the Dataset

The dataset is provided in PyTorch format and is intended for use with PyTorch Geometric.

Example:

```python
import torch

graphs = torch.load(
    "data/all_graphs_Multi_domain.pt",
    map_location="cpu",
    weights_only=False
)

print("Number of graphs:", len(graphs))
print("First graph:", graphs[0])
```

Each graph contains node features, edge connectivity, edge attributes, and a graph-level domain label.

## 7. Annotations

The repository provides separate CSV annotation files for:

- **Component annotations:** Bond Graph component labels.
- **Edge annotations:** Graph connection information and associated causality annotations.

The annotation files are organized by physical domain.

The annotation format and labeling methodology are described in:

- [`documentation/annotation_protocol.md`](documentation/annotation_protocol.md)
- [`documentation/graph_format.md`](documentation/graph_format.md)

## 8. Intended Use

This dataset is intended for research and experimentation in:

- Graph Neural Networks.
- Bond Graph modeling and analysis.
- Physical-system domain classification.
- Graph-based component recognition.
- Structural and causal learning.
- AI-assisted physical-system modeling.

## 9. Citation

If you use this dataset in your research, please cite the dataset publication.

The DOI and formal citation will be added after the dataset has been archived in Zenodo.

## 10. License

The dataset license will be specified before the official public release.

## 11. Contact

For questions or further information concerning this dataset, please contact the authors through the associated research publication.
