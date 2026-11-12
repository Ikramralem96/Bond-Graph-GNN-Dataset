# Dataset Statistics

## 1. Overview

The Bond Graph GNN dataset contains **3,621 graph samples** representing physical systems from five different domains.

## 2. Domain Distribution

| Domain | Label | Number of Graphs | Percentage |
|---|---:|---:|---:|
| Electrical | 0 | 993 | 27.42% |
| Mechanical | 1 | 774 | 21.38% |
| Electromechanical | 2 | 600 | 16.57% |
| Thermal | 3 | 360 | 9.94% |
| Hydraulic | 4 | 894 | 24.69% |
| **Total** | | **3,621** | **100%** |

## 3. Graph Representation

Each graph contains:

- `x`: node feature matrix with 13 component features.
- `edge_index`: graph connectivity information.
- `edge_attr`: edge attributes.
- `y`: physical-domain label.

## 4. Deduplication Statistics

Graph-level duplicate detection is part of the dataset validation process.

The number of unique graphs and duplicate samples will be reported after the deduplication procedure has been independently verified.

## 5. Notes

The statistics presented here describe the current dataset version. Additional statistics may be added after validation of the annotation files and graph structure.
