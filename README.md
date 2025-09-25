# SenNet Demo Notebooks

This interactivity and visual elements in these demo notebooks support spatial analysis in fields computational biology. Click to navigate to the description of each of the notebooks below:

- [demo-search-download-datasets.ipynb](#demo-search-download-datasetsipynb)
- [demo-query-sources.ipynb](#demo-query-sourcesipynb)
- [demo-search-mouse-geomx-data-by-age.ipynb](#demo-search-mouse-geomx-data-by-ageipynb)
- [demo-xenium-reference-dataset.ipynb](#demo-xenium-reference-datasetipynb)
- [demo-transfer-annotations-spatial.ipynb](#demo-transfer-annotations-spatialipynb)
- [demo-xenium-neighbors.ipynb](#demo-xenium-neighborsipynb)
- [demo-xenium-islets-composition.ipynb](#demo-xenium-islets-compositionipynb)
- [demo-affine-transform.ipynb](#demo-affine-transformipynb)
- [demo-multimodal-imaging.ipynb](#demo-multimodal-imagingipynb)
- [demo-scrna-one-donor.ipynb](#demo-scrna-one-donoripynb)
- [demo-visium-explore-spatial.ipynb](#demo-visium-spatialipynb)
- [demo-snrna-seq-all-human-lung.ipynb](#demo-snrna-seq-all-human-lungipynb)


## Setup

This guide helps you set up a Python environment with necessary packages and Jupyter Notebook on a **local computer**. If you wish to use Visual Studio Code or Remote Jupyter Server, it would require additional steps not detailed here to enable interactive features.

#### Installation prerequisites

- Python 3.9
- Terminal app or Command Prompt

#### Step 1: Get a copy of this repository

Make a new directory and navigate to it, for example, on Mac run in the Terminal app:

    mkdir -p ~/some/path/
    cd ~/some/path/

Clone the repository:

    git clone https://github.com/TheJacksonLaboratory/sennet-demo.git

<details closed><summary>Authentication</summary><p>

Note that until this repository is public, the user must login, e.g., as below, and then following prompts to login with HTTPS via a web browser and a code:

    conda config --remove channels defaults
    conda config --add channels conda-forge
    conda config --set channel_priority strict
    conda install gh
    gh auth login

</p></details>


#### Step 2, optional: Create and activate a virtual environment

<details closed><summary>Setup environmet</summary><p>
Using conda is a bit easier:

    conda create --name sennet-demo-env-a "python==3.9"
    conda activate sennet-demo-env-a

    ## To remove environment
    # conda env remove --name sennet-demo-env-a

or

If Python 3.9 not installed, then install it and create a virtual environment (https://docs.python.org/3/tutorial/venv.html)

    python3.9 -m venv sennet-demo-env-a
    source myenv/bin/activate

</p></details>


#### Step 3: Install packages

    # For environment A: most notebooks
    pip install jupyter "notebook>=7" numpy pandas "pyarrow<=20.0.0" 'vitessce[all]' scanpy umap scipy scikit-learn matplotlib globus-cli atlas-consortia-clt requests tifffile imagecodecs igraph leidenalg harmonypy celltypist

or

    # For environment B: demo-affine-transform.ipynb
    pip install jupyter "notebook>=7" "numpy<2.0" pandas "pyarrow<=20.0.0" scanpy umap scipy scikit-learn matplotlib requests fsspec zarr xarray "distributed<=2023" kerchunk tifffile imagecodecs stardist==0.8.5 tensorflow==2.14 igraph leidenalg anndata dask aiohttp==3.8.6

<details closed><summary>Packages usage</summary><p>

|Package    |Demo<br>search<br>portal|Demo<br>multimodal<br>imaging|Demo<br>Xenium<br>reference|Demo<br>Xenium<br>annotate|Demo<br>Visium<br>spatial|Demo<br>query<br>sources|Demo<br>GeoMx<br>search|Demo<br>Xenium<br>neighbors|Demo<br>Xenium<br>Islets|Demo<br>scRNAseq<br>pancreas|Demo<br>affine<br>transform|Demo<br>snRNAseq<br>human<br>lung| ... |
|----------------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|vitessce              |     | 🟢  |     |     |     |     |     |     |    |     |     |     |     |
|requests              | 🟢  |     |     |     |     |  🟢 |  🟢 |     |    |     |  🟢 |  🟢  |     |
|pandas                | 🟢  |     | 🟢  | 🟢  | 🟢  | 🟢  |  🟢 | 🟢 | 🟢 | 🟢 |  🟢 |  🟢  |     |
|matplotlib            |     |     | 🟢  | 🟢  | 🟢  | 🟢  |     | 🟢  | 🟢 | 🟢  |  🟢 |  🟢  |     |
|numpy                 |     | 🟢  | 🟢  | 🟢  | 🟢  |     |     | 🟢 | 🟢 | 🟢  | 🟢  |  🟢  |     |
|scanpy                |     |     | 🟢  | 🟢  | 🟢  |     |     | 🟢 | 🟢 |  🟢 | 🟢 |  🟢  |     |
|scipy                 |     |     | 🟢  | 🟢  | 🟢  |     |     | 🟢  | 🟢 |     |     |     |     |
|tifffile              |     |     |     | 🟢  | 🟢  |     |     |  🟢 | 🟢 |     |  🟢 |     |     |
|fsspec                |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|xarray                |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|zarr                  |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|kerchunk              |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|stardist              |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|tensorflow            |     |     |     |     |     |      |    |     |    |     |  🟢 |     |     |
|umap                  |     |     | 🟡  |     |     |     |     |     |    |     |     |     |     |
|sklearn               |     |     | 🟡  |     |     |     |     |     |    |     |     |     |     |
|globus-cli            | 🟡  |     |     |     |     |     |     |     |    |     |     |     |     |
|atlas-consortia-clt   |     |     |     |     |     |      | 🟡 |     |    |     |     |     |     |
|harmonypy             |     |     |     |     |     |      |    |     |    |     |     |  🟢  |     |
|celltypist            |     |     |     |     |     |      |    |     |    |     |     |  🟢  |     |

🟢 - required<br>
🟡 - optional

</p></details>

#### 🚀 Step 4: Launch jupyter

    jupyter notebook

To explore the notebook(s) and data:

1. Navigate to the notebook in JupyterLab or Jupyter Notebook.
2. Follow the guided sections to visualize and interpret the data.
3. Use the provided widgets to filter by sample, cell type, or metadata, and produce any custom plots.

## Notebooks overview

### demo-search-download-datasets.ipynb

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

[Click here to view Demo](notebooks/demo-search-download-datasets.ipynb)


### demo-query-sources.ipynb

The task is find Donor metadata associated with each of the SenNet datasets of interest. The SenNet Data Sharing Portal (https://data.sennetconsortium.org/) is used to query IDs of all kidney histology datasets generated by UConn Health TMC, resulting in a list of 43 dataset **`sennet_id`**, e.g., `SNT224.LSLK.429`. The list was downloaded in TSV file format. The downloaded TSV file is loaded with a python, then metadata is retrieved via API for each SenNet ID of interest and compiled it into a table.

Lastly, the notebook explores several ways to visualize the obtained Donor metadata.

[Click here to view Demo](notebooks/demo-query-sources.ipynb)


### demo-search-mouse-geomx-data-by-age.ipynb

The focus of this vignette is using the SenNet Search API to find datasets of a particular type (in this example, GeoMx NGS), then using `pandas` to further filter those datasets based on existing dataset attributes (e.g. source species) as well as derived information (e.g. age). In this notebook, all GeoMx datasets are queried using the API and parsed by those from human- or mouse-derived sources. Mouse datasets are further filtered to include only data from mice older than 12 months. The latter of these filters requires age to be calculated from existing source metadata fields `date_of_birth_or_fertilization` and `date_of_death`.

Filtered `pandas` dataframes can be used to generate a customized manifest text file to download data using the SenNet Command Line Transfer tool.

[Click here to view Demo](notebooks/demo-search-mouse-geomx-data-by-age.ipynb)


### demo-xenium-reference-dataset.ipynb

This Jupyter Notebook is part of a scientific data analysis pipeline designed to process and visualize spatial transcriptomics data from 28 human pancreas tissue samples profiled using the **Xenium 300-gene panel** (see collection `SNT793.SZRS.468`). The notebook focuses on **annotated cell types**, **sample-level metadata**, and **quantitative imaging-derived metrics** to provide a comprehensive view of tissue architecture and cellular diversity.

> Users are not required to run the dataset construction steps. Instead, a pre-annotated reference dataset is provided for direct exploration.

> Spatial coordinates and image overlays for each sample are not included in the reference dataset.

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

[Click here to view Demo](notebooks/demo-xenium-reference-dataset.ipynb)


### demo-transfer-annotations-spatial.ipynb

This notebook explores a normal human pancreas sample from a 69-year-old donor (Data IDs: `SNT576.PXPP.452`, `SNT484.VLRN.777`). The demo emphasizes the power of spatial visualizations in understanding cellular heterogeneity and tissue organization. By leveraging spatial transcriptomics and multiplex immunofluorescence (mIF) data, researchers can explore cell types, phenotypic markers, and gene expression profiles in their native spatial context. This approach is particularly valuable for studying complex tissues, such as the pancreas.

The notebook demonstrates how to visualize cell types, such as Acinar, Ductal, and Endocrine cells, alongside markers like p16 from mIF (PhenoCycler) and genes such as MUC5AC and MUC5B. These visualizations can be tailored to show cells with their boundaries or as dots overlayed on morphology images. The ability to toggle between these modes provides flexibility in highlighting specific spatial features or simplifying the visualization for broader patterns.

Such spatial visualizations are invaluable to the research community for several reasons. First, they enable the identification of spatially distinct cell populations and their functional roles within tissues. For example, the expression of p16, a marker associated with cellular senescence, can be mapped to specific regions, providing insights into aging or disease processes. Similarly, genes like MUC5AC and MUC5B, which are involved in mucin production, can be studied in the context of their spatial distribution and association with cell types.

The ability to subset data by spatial location or cell type provides a powerful tool for focusing on specific regions or populations of interest. This targeted approach is particularly useful for studying rare cell types, localized disease processes, or regions of high marker expression.

[Click here to view Demo](notebooks/demo-transfer-annotations-spatial.ipynb)


### demo-xenium-neighbors.ipynb

This notebook investigates a normal human pancreas sample from a 69-year-old donor (Data ID: `SNT576.PXPP.452`) using spatial transcriptomics data. It demonstrates a fast and scalable spatial neighborhood search to identify cells of interest and their local microenvironments. The workflow includes locating and visualizing specific cell types within the tissue's spatial layout.

Two illustrative examples are provided: (1) Identification of endocrine cells neighboring abnormal ductal cells.; (2) Analysis of gene expression differences between p16-high cells and their spatial neighbors, including characterization of surrounding cell types.

The notebook guides the user from data access through spatial querying to biological interpretation, making it a practical tool for researchers exploring cell-cell interactions in situ.

[Click here to view Demo](demo-xenium-neighbors.ipynb)


### demo-xenium-islets-composition.ipynb

This notebook analyzes a normal human pancreas sample from a 69-year-old donor (Data ID: `SNT576.PXPP.452`) using spatial transcriptomics data.

It introduces a spatial search strategy to identify endocrine cells that neighbor other endocrine cells, enabling the construction of a neighborhood graph to detect pancreatic islets. The graph-based approach is highly configurable, allowing users to define connectivity thresholds and apply filters to refine islet identification.

The primary objective is to quantify the proportion of each endocrine cell type within individual islets. Visualizations such as heatmaps and dendrograms reveal that most islets are dominated by a single cell type—typically alpha, beta, or gamma—rather than exhibiting a mixed composition.

Secondary analyses include identifying the largest islet in the tissue and the largest beta-dominant islet, offering insights into islet organization and potential functional relevance.

Finally, the notebook demonstrates how to extend the framework to analyze non-endocrine cells located within or adjacent to islets, showcasing its flexibility for broader spatial tissue analysis.

[Click here to view Demo](notebooks/demo-xenium-islets-composition.ipynb)


### demo-affine-transform.ipynb

This research data demo integrates conventional histological imaging with advanced spatial transcriptomics to investigate normal human pancreas tissue from a 69-year-old donor (Data IDs for Xenium and H&E: `SNT576.PXPP.452`, `SNT443.KFNS.239`). Characterizing healthy pancreatic architecture provides a foundation for understanding pathogenesis in diabetes, pancreatic cancer, and related disorders.

The demo combines two complementary imaging modalities: H&E histology, which uses chemical stains to visualize tissue morphology, and Xenium spatial genomics, which quantifies gene expression in situ while preserving spatial context. A key technical challenge is reconciling the distinct coordinate systems used by these platforms. This is addressed through mathematical non-rigid affine transformations that enable precise spatial alignment of gene expression data with histological features.

The notebook demonstrates how to extract a high-resolution image patch, perform nuclear segmentation using StarDist, overlay the segmented nuclei on the H&E image, and transform their coordinates into the Xenium spatial framework. It concludes by visualizing the transformed nuclei overlaid on native Xenium cell boundaries, enabling direct comparison between histological and molecular features.

This workflow also showcases a streaming-based data access strategy that allows researchers to interact with large-scale microscopy datasets without downloading multi-gigabyte files. Through remote programmatic access to the SenNet Data Sharing Portal, users can retrieve specific resolution levels on demand. This integrated approach facilitates the construction of spatially resolved maps that link tissue morphology with gene activity, advancing mechanistic insights into tissue organization and function.

[Click here to view Demo](demo-affine-transform.ipynb)


### demo-multimodal-imaging.ipynb

This notebook explores a normal human pancreas tissue sample from a 69-year-old donor (Data IDs: `SNT574.MMQC.683`, `SNT594.JCFN.856`, `SNT227.HLMG.672`). The selected tissue region features a large mucinous pancreatic duct expressing keratin 19 (KRT19), a surrounding layer of endocrine alpha cells, and additional layers of endothelial cells, fibroblasts, and other stromal components.

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

[Click here to view Demo](notebooks/demo-multimodal-imaging.ipynb)


### demo-scrna-one-donor.ipynb

This notebook enhances the interpretability of SenNet datasets for aging and disease research. It outlines a preprocessing pipeline that integrates three SenNet datasets: `SNT268.LXPG.784` ('PL0006PADISNR'), `SNT324.BDTT.263` ('PL0006PADDU'), and `SNT469.JJLS.674` ('PL0006PADAC'). The workflow demonstrates how to efficiently download, harmonize, and annotate single-cell RNA-seq data across multiple sources, ensuring consistency in cell type classification.

To facilitate reproducibility, the notebook includes code for loading and preprocessing the datasets using filtered **`h5`** files generated by 10x Genomics Cell Ranger. This approach provides a practical template for handling diverse SenNet data in a unified manner.

As a downstream application, the annotated data is used to compute gene scores based on the SenMayo gene set, stratifying cells into low, intermediate, and high score bins. These bins reveal distinct shifts in cell type composition, offering insights into cellular heterogeneity and potential biological relevance.

[Click here to view Demo](demo-scrna-one-donor.ipynb)


### demo-visium-spatial.ipynb

This notebook is designed to analyze spatial transcriptomics data from the pancreas tissue sample of a 69-year-old donor, JDC-WP-012-w (`SNT544.XHGB.538`), using the Visium platform. The Visium platform enables researchers to study gene expression patterns in their spatial context, preserving the spatial organization of tissues. This is particularly important for understanding complex biological processes, tissue heterogeneity, and cellular interactions within the pancreas, which plays a critical role in metabolic regulation and disease progression.

The pancreas is a highly specialized organ composed of distinct regions, including the endocrine Islets of Langerhans, exocrine acinar cells, and ductal structures. Spatial transcriptomics allows researchers to characterize these regions at the molecular level, identifying spatially distinct gene expression patterns. In this notebook, the dataset is processed to identify clusters of Visium spots, visualize spatial gene expression, and explore transcriptional topics associated with specific biological processes or cell states. For example, topics such as Islet of Langerhans, Acinar to ductal metaplasia (ADM), and Vascular structures are visualized to understand their spatial organization and associated gene sets.

The notebook leverages computational tools like scanpy for preprocessing, dimensionality reduction (PCA and UMAP), clustering (Leiden algorithm), and differential expression analysis. It also integrates STdeconvolve, a reference-free deconvolution tool, to identify latent transcriptional topics that represent co-expressed gene groups. These topics provide insights into spatially organized biological processes, such as endocrine function in the Islets of Langerhans or pathological changes like ADM, which is associated with pancreatic disease and cancer.

[Click here to view Demo](notebooks/demo-visium-spatial.ipynb)


### demo-snrna-seq-all-human-lung.ipynb

This notebook walks step-by-step through querying **all** human lung single-nucleus RNA-sequencing datasets using `requests` against SenNet APIs; downloading `h5ad` data files for **all** existing donors directly from the SenNet portal; linking source and assay metadata; and undertaking processing, integration, and annotation of datasets.

Often, it is useful to integrate datasets across samples to compare similar cell populations between batches. Various algorithms aim to mitigate "batch effects" that cause misalignment of otherwise comparable expression profiles. The `harmonypy` package iteratively adjusts the principal components of concatenated expression data until a convergence is reached, indicating that batches have been sufficiently "aligned". In this tutorial, over 250,000 cells representing 66 donors are pre-processed and integrated. The `celltypist` package is then used to predict cell types in the data by comparing to a model based on the Human Lung Cell Atlas. Finally, the resulting integration and annotation are used to compare how proportions of cell types in the human lung change across age groups.

[Click here to view Demo](notebooks/demo-snrna-seq-all-human-lung.ipynb)
