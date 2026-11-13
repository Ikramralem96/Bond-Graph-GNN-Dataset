# Annotation Protocol

## 1. Overview

This document describes the annotation protocol used to construct the Bond Graph dataset.

The annotation process covers two main aspects:

- Bond Graph component annotation.
- Graph connection and causality annotation.

The annotations are organized according to five physical domains: Electrical, Mechanical, Electromechanical, Thermal, and Hydraulic.

## 2. Component Annotation

### 2.1 Component Classes

Each Bond Graph image is annotated according to the 13 component classes considered in this dataset:

| Label | Component |
|---|---|
| R | Resistance |
| C | Capacitance |
| I | Inertia |
| Se | Effort Source |
| Sf | Flow Source |
| J0 | 0-junction |
| J1 | 1-junction |
| TF | Transformer |
| GY | Gyrator |
| MTF | Modulated Transformer |
| MGY | Modulated Gyrator |
| Df | Flow Detector |
| De | Effort Detector |

### 2.2 Annotation Format

Component annotations are stored in CSV files organized by physical domain.

The component annotation files follow the naming convention:

`components_labels_<Domain>.csv`

They are stored in:

`data/annotations/components/`

Each row corresponds to an annotated Bond Graph image.

The annotation table contains the following information:

- `filename`: name of the annotated image.
- `Domain`: physical domain associated with the image.
- Component columns: the 13 component classes listed above.

### 2.3 Component Occurrences

The component columns record the number of occurrences of each component class in the corresponding image.

A value of zero indicates that the component does not occur in the image, while a positive integer represents its number of occurrences.

## 3. Graph Connection and Causality Annotation

### 3.1 Edge Annotation

Graph connections are annotated separately from component annotations.

The edge annotation files follow the naming convention:

`edges_annotations_<Domain>.csv`

They are stored in:

`data/annotations/edges/`

Each row represents an annotated connection between two Bond Graph components.

The edge annotation files contain the following fields:

- `graph_id`: identifier of the annotated graph or image.
- `source`: source component or node of the connection.
- `target`: target component or node of the connection.
- `causality`: causality-related annotation associated with the connection.
- `domain`: physical domain associated with the graph.

### 3.2 Power Direction and Causality

The annotation workflow distinguishes between two graphical concepts:

- **Power direction:** represented by the half-arrow on a Bond Graph bond.
- **Causality:** represented by the causal stroke.

These two concepts are distinct and describe different aspects of Bond Graph structure.

The edge annotation files use the following causality labels:

- `at_source`
- `at_target`

These labels encode the endpoint associated with the causality annotation.

Power direction and causality should not be interpreted as equivalent information.

## 4. Domain Organization

The annotation files are organized according to the five physical domains.

| Domain | Component Annotations | Edge Annotations |
|---|---|---|
| Electrical | `components/components_labels_Electrical.csv` | `edges/edges_annotations_Electrical.csv` |
| Mechanical | `components/components_labels_Mechanical.csv` | `edges/edges_annotations_Mechanical.csv` |
| Electromechanical | `components/components_labels_Electromechanical.csv` | `edges/edges_annotations_Electromechanical.csv` |
| Thermal | `components/components_labels_Thermal.csv` | `edges/edges_annotations_Thermal.csv` |
| Hydraulic | `components/components_labels_Hydraulic.csv` | `edges/edges_annotations_Hydraulic.csv` |

All annotation files are stored under:

`data/annotations/`

## 5. Duplicate Image Handling

Duplicate images are identified during dataset preparation using image similarity and hashing procedures.

When duplicate images are identified, existing annotations can be reused to maintain consistency across the dataset.

The annotation CSV files preserve the image-level records associated with the annotation process.

This procedure helps maintain annotation consistency while supporting dataset organization and preparation.

## 6. Annotation Organization

The annotation files are stored separately from the main PyTorch Geometric dataset.

This separation allows researchers to inspect component-level and connection-level annotations independently.

The component annotations describe the occurrence of Bond Graph components, while the edge annotations provide information about graph connectivity and causality.

## 7. Notes

The component annotation files describe component occurrences in each image.

The edge annotation files describe graph connections and their associated causality information.

The annotation files are provided separately for each physical domain to facilitate data inspection, processing, and reuse.

Researchers should refer to the corresponding CSV files and the annotation conventions described in this document when using the dataset.
