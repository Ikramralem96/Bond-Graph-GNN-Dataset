# Graph Data Format

## 1. Overview

The Bond Graph dataset represents physical systems as graph structures using the PyTorch Geometric data format.

Each graph describes a Bond Graph model and contains node features, connectivity information, edge attributes, and a physical-domain label.

## 2. Graph Representation

Each graph is represented by the following attributes:

| Attribute | Description |
|---|---|
| `x` | Node feature matrix |
| `edge_index` | Graph connectivity matrix |
| `edge_attr` | Edge attribute matrix |
| `y` | Graph-level physical-domain label |

A graph can be represented as:

\[
G = (X, E, A, y)
\]

where:

- \(X\) represents the node features.
- \(E\) represents the graph connectivity.
- \(A\) represents the edge attributes.
- \(y\) represents the physical-domain class.

## 3. Node Features

The node feature matrix is stored in the `x` attribute.

Each node is represented by a feature vector containing 13 features corresponding to the Bond Graph component classes:

`R, C, I, Se, Sf, J0, J1, TF, GY, MTF, MGY, Df, De`.

The node feature matrix has the following general shape:

\[
X \in \mathbb{R}^{N \times 13}
\]

where \(N\) is the number of nodes in the graph.

## 4. Graph Connectivity

The `edge_index` attribute describes the connections between nodes.

It follows the PyTorch Geometric connectivity convention, with two rows representing the source and target node indices.

Its general shape is:

\[
edge\_index \in \mathbb{N}^{2 \times E}
\]

where \(E\) represents the number of edges.

## 5. Edge Attributes

The `edge_attr` attribute stores the edge-related information associated with graph connections.

In the current dataset, each edge is represented using one attribute.

Its general shape is:

\[
edge\_attr \in \mathbb{R}^{E \times 1}
\]

The detailed interpretation and encoding of edge attributes will be described in the annotation documentation.

## 6. Graph-Level Labels

The `y` attribute represents the physical domain associated with each graph.

The domain labels are encoded as follows:

| Label | Physical Domain |
|---:|---|
| 0 | Electrical |
| 1 | Mechanical |
| 2 | Electromechanical |
| 3 | Thermal |
| 4 | Hydraulic |

## 7. Loading a Graph

The dataset can be loaded using PyTorch:

```python
import torch

graphs = torch.load(
    "data/all_graphs_Multi_domain.pt",
    map_location="cpu",
    weights_only=False
)

graph = graphs[0]

print("Node features:", graph.x.shape)
print("Connectivity:", graph.edge_index.shape)
print("Edge attributes:", graph.edge_attr.shape)
print("Domain label:", graph.y)
```

## 8. Annotation Files

Component and causality annotations are maintained separately from the main graph dataset.

These annotations provide additional information about Bond Graph components and connections.

Their organization and labeling conventions are described in the annotation documentation.

## 9. Notes

The dataset contains graph-level domain labels in the main `.pt` file.

Node-level component annotations and edge-level causality annotations are maintained separately and should not be assumed to be included in every graph object.

The graph representation is intended to support research on graph-based learning, Bond Graph analysis, and physical-system classification.
