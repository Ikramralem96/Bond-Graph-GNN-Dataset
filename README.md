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

The current dataset contains **3,621 graph samples**.

The five physical domains are encoded using the following labels:

| Label | Physical Domain |
|:---:|---|
| 0 | Electrical |
| 1 | Mechanical |
| 2 | Electromechanical |
| 3 | Thermal |
| 4 | Hydraulic |

The dataset includes Bond Graph structures represented in PyTorch Geometric format.

## 3. Graph Representation

Each graph is represented using the following attributes:

| Attribute | Description |
|---|---|
| `x` | Node feature matrix with 13 features per node |
| `edge_index` | Connectivity information between graph nodes |
| `edge_attr` | Edge attributes |
| `y` | Physical-domain class label |

The component and causality annotations are maintained in separate files and will be documented in the annotation documentation.

## 4. Dataset File

The main dataset file is:

`all_graphs_Multi_domain.pt`

It contains the collection of graph samples used for multi-domain Bond Graph research.

## 5. Repository Structure

The repository is organized as follows:

```text
Bond-Graph-GNN-Dataset/
│
├── README.md
├── LICENSE
├── CITATION.cff
│
├── data/
│   ├── all_graphs_Multi_domain.pt
│   └── annotations/
│
├── documentation/
│   ├── graph_format.md
│   ├── annotation_protocol.md
│   └── dataset_statistics.md
│
└── code/
    ├── graph_generation.py
    ├── preprocessing.py
    └── evaluation.py
```

This structure will be completed progressively as the dataset documentation and supplementary files are prepared.

## 6. Loading the Dataset

The dataset is provided in PyTorch format and is intended to be used with PyTorch Geometric.

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

## 7. Annotations

Separate annotation files are used to document:

- Bond Graph component labels.
- Graph connection information.
- Causality annotations.

The annotation format and labeling methodology will be described in the accompanying documentation.

## 8. Intended Use

This dataset is intended for research and experimentation in:

- Graph Neural Networks.
- Bond Graph modeling and analysis.
- Physical-system domain classification.
- Graph-based component recognition.
- Structural and causal learning.
- AI-assisted physical-system modeling.

## 9. Citation

A formal citation and DOI will be provided after the dataset has been archived in Zenodo.

## 10. License

The dataset license will be specified before the official public release.

## 11. Contact

For questions or information concerning this dataset, please contact the authors through the associated research publication.
