# SenNet Demo Notebooks

This interactivity and visual elements in these demo notebooks support spatial analysis in fields computational biology. Click to navigate to the description of each of the notebooks below:

- [demo-search-download-datasets.ipynb](#1-demo-search-download-datasetsipynb)
- [demo-multimodal-imaging.ipynb](#2-demo-multimodal-imagingipynb)
- [demo-xenium-reference-dataset.ipynb](#3-demo-xenium-reference-datasetipynb)
- [demo-transfer-annotations-spatial.ipynb](#4-demo-transfer-annotations-spatialipynb)
- [demo-visium-explore-spatial.ipynb](#5-demo-visium-explore-spatialipynb)


## Setup

This guide helps you set up a Python environment with necessary packages and Jupyter Notebook on a **local computer**. If you wish to use Visual Studio Code or Remote Jupyter Server, it would require additional steps not detailed here to enable interactive features.

#### Installation prerequisites

- Python 3.8 or higher
- curl: the examples use this unitility to download example data

#### 🛠️ Step 1 (optional): Create and activate a virtual environment

https://docs.python.org/3/tutorial/venv.html

#### 🛠️ Step 2: Install packages

    pip install jupyter numpy pandas 'vitessce[all]' scanpy umap scipy scikit-learn matplotlib tifffile globus-cli


|Package    |Demo 1|Demo 2|Demo 3|Demo 4|Demo 5| ... |
|-----------|-----|-----|-----|-----|-----|-----|
|vitessce   |     | 🟢  |     |     |     |     |
|numpy      |     | 🟢  | 🟢  | 🟢  | 🟢  |     |
|pandas     | 🟢  |     | 🟢  | 🟢  | 🟢  |     |
|scanpy     |     |     | 🟢  | 🟢  | 🟢  |     |
|umap       |     |     | 🟡  |     |     |     |
|sklearn    |     |     | 🟡  |     |     |     |
|scipy      |     |     | 🟢  | 🟢  | 🟢  |     |
|matplotlib |     |     | 🟢  | 🟢  | 🟢  |     |
|tifffile   |     |     |     | 🟢  | 🟢  |     |
|globus-cli | 🟡  |     |     |     |     |     |

🟢 - required;
🟡 - optional;


#### Step 3. Download the notebook(s) to a local computer

    ./notebooks/demo-multimodal-imaging.ipynb

#### 🚀 Step 3: Launch jupyter

    jupyter notebook

To explore the notebook(s) and data:

1. Open the notebook in JupyterLab or Jupyter Notebook.
2. Follow the guided sections to visualize and interpret the data.
3. Use the provided widgets to filter by sample, cell type, or metadata, and produce any custom plots.


## 1. demo-search-download-datasets.ipynb

This demo is designed to demonstrate how to search, filter from the SenNet Data Sharing Portal, and then download datasets programmatically for customized analysis. The portal is a centralized platform for sharing high-resolution datasets related to cellular senescence research, including transcriptomics, proteomics, and imaging data. This notebook is designed for researchers working with large-scale datasets who need efficient tools for data discovery, retrieval, and analysis.

Use cases described here are: metadata exploration, programmatic data access, file download automation, integration with Globus.

The demo includes:

* Introduction: Provides an overview of the SenNet Data Sharing Portal, its purpose, and features, such as interactive and programmatic data access.
* Description: Explains the workflow for filtering and exporting datasets using the portal's interface, including selecting assay types and exporting dataset IDs to a TSV file.
* Exploring Data Programmatically: Demonstrates how to load the exported TSV file using Python's pandas library and retrieve metadata for datasets.
* API Functions: Includes Python functions to retrieve derived datasets for a given UUID, and find processed files associated with derived datasets.

Examples:
1. Retrieving and accessing derived datasets programmatically using specific SenNet IDs.
2. Accessing Raw Dataset Files using the Globus CLI, including listing and transferring files.


## 2. demo-multimodal-imaging.ipynb

### Pancreatic Tissue Imaging Exploration

This notebook explores a normal human pancreas sample from a 69-year-old donor (Data IDs: `SNT574.MMQC.683`, `SNT594.JCFN.856`, `SNT227.HLMG.672`). The selected tissue region features a large mucinous pancreatic duct expressing keratin 19 (KRT19), a surrounding layer of endocrine alpha cells, and additional layers of endothelial cells, fibroblasts, and other stromal components.

Why This Case is Interesting? - This case offers a unique opportunity to study:

- **Transitional Zonation**: From ductal epithelium to endocrine islets to stromal tissue—ideal for analyzing microenvironmental gradients.
- **KRT19 Expression**: A ductal marker often linked to progenitor-like states, providing a healthy baseline for comparison with disease states like PDAC.
- **Alpha Cell Localization**: Raises questions about islet neogenesis, cellular plasticity, or developmental remnants.
- **Stromal Interactions**: The presence of fibroblasts and endothelial cells supports exploration of cell-cell and cell-matrix interactions.

This notebook integrates multiple imaging techniques: Hematoxylin & Eosin (H&E) highlights general tissue architecture. Nuclei: blue/purple; Cytoplasm/ECM: pink. Immunofluorescence (IF) visualizes specific proteins (e.g., Keratin 19, Glucagon, Insulin, CD31). Reveals molecular and functional cell details.
Cell Mask (Bitmask) is the segmentation of individual cells, which enables spatial and morphological analysis.

**Interactive Exploration with Vitessce**. To ensure accurate cross-modality comparisons, the notebook applies pre-computed transformation matrices that rotate, scale, shear, and translate iamges. This aligns all imaging modalities to a common coordinate space (here, Xenium space). The notebook uses the Vitessce viewer to enable:

- Layer toggling (e.g., IF, H&E, masks)
- Zooming and panning for fine detail inspection
- Channel and color control
- Opacity adjustment for blending modalities


## 3. demo-xenium-reference-dataset.ipynb

This Jupyter Notebook is part of a scientific data analysis pipeline designed to process and visualize spatial transcriptomics data from 28 human pancreas tissue samples profiled using the **Xenium 300-gene panel** (see collection `SNT793.SZRS.468`). The notebook focuses on **annotated cell types**, **sample-level metadata**, and **quantitative imaging-derived metrics** to provide a comprehensive view of tissue architecture and cellular diversity.

> ⚠️ Note: Users are not required to run the dataset construction steps. Instead, a pre-annotated reference dataset is provided for direct exploration.

> ⚠️ Note: Spatial coordinates and image overlays for each sample are not included in the reference dataset.

This Demo is aimed at:
- Demonstrating the **construction process** of a reference dataset.
- Exploration of **annotated cell types** and ***metadata** across 28 pancreas samples.
- Visualization and subsetting of **gene expression** across cell types.


The reference dataset includes:
- **28 pancreas tissue samples** from diverse donors.
- **Cell-level annotations** based on gene expression and spatial context.
- **Metadata** such as donor age, sex, disease status, and sample quality.
- **Quantitative metrics**: cell counts and morphological features.

Cell type annotation is a cornerstone of spatial transcriptomics analysis. It allows us to map tissue architecture and identify functional zones (e.g., islets of Langerhans vs. exocrine tissue), compare cellular composition across donors. generate hypotheses about cell-cell interactions, signaling pathways, and disease mechanisms. Here are some key questions this notebook helps address:

- Can we identify endocrine and exocrine cell types and their subtypes?
- What genes are expressed in different cell types?
- How does cell type composition vary across donors or conditions?
- Which cell types dominate in different regions of the pancreas

Features of the Noteboo include code to download the annotated dataset for analysis, precomputed UMAP layout of cell types, summary statistics and barplots of cell type distributions, metadata filtering and subgroup comparisons, marker summary dot plots and violin plots.

This reference dataset lays the groundwork for: Machine learning models to predict disease states, Cross-tissue comparisons using harmonized annotations, Integration with other omics layers (e.g., proteomics, epigenomics).


## 4. demo-transfer-annotations-spatial.ipynb

This notebook explores a normal human pancreas sample from a 69-year-old donor (Data IDs: `SNT576.PXPP.452`, `SNT484.VLRN.777`). The demo emphasizes the power of spatial visualizations in understanding cellular heterogeneity and tissue organization. By leveraging spatial transcriptomics and multiplex immunofluorescence (mIF) data, researchers can explore cell types, phenotypic markers, and gene expression profiles in their native spatial context. This approach is particularly valuable for studying complex tissues, such as the pancreas.

The notebook demonstrates how to visualize cell types, such as Acinar, Ductal, and Endocrine cells, alongside markers like p16 from mIF (PhenoCycler) and genes such as MUC5AC and MUC5B. These visualizations can be tailored to show cells with their boundaries or as dots overlayed on morphology images. The ability to toggle between these modes provides flexibility in highlighting specific spatial features or simplifying the visualization for broader patterns.

Such spatial visualizations are invaluable to the research community for several reasons. First, they enable the identification of spatially distinct cell populations and their functional roles within tissues. For example, the expression of p16, a marker associated with cellular senescence, can be mapped to specific regions, providing insights into aging or disease processes. Similarly, genes like MUC5AC and MUC5B, which are involved in mucin production, can be studied in the context of their spatial distribution and association with cell types.

The ability to subset data by spatial location or cell type provides a powerful tool for focusing on specific regions or populations of interest. This targeted approach is particularly useful for studying rare cell types, localized disease processes, or regions of high marker expression.


## 5. demo-visium-explore-spatial.ipynb

TODO
