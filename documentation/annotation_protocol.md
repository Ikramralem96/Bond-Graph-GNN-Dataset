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

They contain information describing the connections between Bond Graph components.

The annotation fields include:

- `source`: source component or node.
- `target`: target component or node.
- `causality`: causality-related annotation.
- `domain`: associated physical domain.

### 3.2 Power Direction and Causality

The annotation workflow distinguishes between two graphical concepts:

- **Power direction:** represented by the half-arrow on a Bond Graph bond.
- **Causality:** represented by the causal stroke.

These two concepts are annotated separately because they represent different aspects of Bond Graph structure.

The detailed encoding of causality labels is defined by the edge annotation files.

## 4. Domain Organization

The annotation files are organized according to the five physical domains:

| Domain | Component annotations | Edge annotations |
|---|---|---|
| Electrical | `components_labels_Electrical.csv` | `edges_annotations_Electrical.csv` |
| Mechanical | `components_labels_Mechanical.csv` | `edges_annotations_Mechanical.csv` |
| Electromechanical | `components_labels_Electromechanical.csv` | `edges_annotations_Electromechanical.csv` |
| Thermal | `components_labels_Thermal.csv` | `edges_annotations_Thermal.csv` |
| Hydraulic | `components_labels_Hydraulic.csv` | `edges_annotations_Hydraulic.csv` |

## 5. Duplicate Image Handling

Duplicate images are identified during dataset preparation using image similarity and hashing procedures.

When duplicate images are identified, their existing annotations are reused rather than independently creating inconsistent labels.

The annotation CSV files retain the image-level records used by the annotation workflow.

## 6. Annotation Organization

The annotation files are stored separately from the main PyTorch Geometric dataset.

This separation allows researchers to inspect component-level and connection-level annotations independently.

## 7. Notes

The component annotation files describe component occurrences in each image.

The edge annotation files describe graph connections and associated causality information.

Researchers should consult the corresponding CSV files when additional annotation details are required.

The exact label encoding and annotation conventions should be interpreted according to the supplied annotation files.
