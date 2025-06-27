# SenNet Demo Notebooks


## 1. demo-multimodal-imaging.ipynb

### 🧬 Pancreatic Tissue Imaging Exploration

#### Case Overview

This notebook explores a **normal human pancreas** sample from a 69-year-old donor (Data IDs: `SNT574.MMQC.683`, `SNT594.JCFN.856`, `SNT227.HLMG.672`). The selected tissue region features:

- A **large mucinous pancreatic duct** expressing **keratin 19 (KRT19)**.
- A surrounding layer of **endocrine alpha cells**.
- Additional layers of **endothelial cells**, **fibroblasts**, and other **stromal components**.

#### Why This Case is Interesting

This case offers a unique opportunity to study:

- **Transitional Zonation**: From ductal epithelium to endocrine islets to stromal tissue—ideal for analyzing microenvironmental gradients.
- **KRT19 Expression**: A ductal marker often linked to progenitor-like states, providing a healthy baseline for comparison with disease states like PDAC.
- **Alpha Cell Localization**: Raises questions about islet neogenesis, cellular plasticity, or developmental remnants.
- **Stromal Interactions**: The presence of fibroblasts and endothelial cells supports exploration of cell-cell and cell-matrix interactions.

#### Imaging Modalities

This notebook integrates multiple imaging techniques:

1. **Hematoxylin & Eosin (H&E)**
   - Highlights general tissue architecture.
   - Nuclei: blue/purple; Cytoplasm/ECM: pink.

2. **Immunofluorescence (IF)**
   - Visualizes specific proteins (e.g., Keratin 19, Glucagon, Insulin, CD31).
   - Reveals molecular and functional cell details.

3. **Cell Mask (Bitmask)**
   - Binary segmentation of individual cells.
   - Enables spatial and morphological analysis.

#### Image Alignment

To ensure accurate cross-modality comparisons, the notebook applies pre-computed transformation matrices that rotate, scale, shear, and translate iamges. This aligns all imaging modalities to a common coordinate space (here, Xenium space).

## Interactive Exploration with Vitessce

The notebook uses the Vitessce viewer to enable:

- Layer toggling (e.g., IF, H&E, masks)
- Zooming and panning for fine detail inspection
- Channel and color control
- Opacity adjustment for blending modalities

This interactivity supports spatial analysis in fields like:

- Aging and senescence research
- Cancer research
- Diabetes and islet biology


This guide helps you set up a Python environment for working with Vitessce, NumPy, and Jupyter Notebook.

#### 📦 Installation prerequisites

- Python 3.8 or higher

#### 🛠️ Step 1 (optional): Create and activate a virtual environment

https://docs.python.org/3/tutorial/venv.html

#### 🛠️ Step 2: Install packages

    pip install numpy jupyter 'vitessce[all]'

#### 💾 Step 3. Download the notebook to a local computer

    ./notebooks/demo-multimodal-imaging.ipynb

#### 🚀 Step 3: Launch jupyter

    jupyter notebook
