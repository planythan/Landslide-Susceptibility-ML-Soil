This repository contains the source code, datasets, and pre-trained models used in our research paper for generating Landslide Susceptibility Maps. The project compares scenarios using 9 and 11 causative factors across various machine learning algorithms.

##  Repository Structure

- `landslide_model.ipynb`: The main Jupyter Notebook containing all 6 cells of the workflow.
- `train.csv` / `test.csv`: The datasets used for training and evaluating the models.
- `exclude1.tif` / `include1.tif`: Raster files for the 9-factor and 11-factor scenarios (used for Frequency Ratio validation).
- `pretrained_models/`: **[IMPORTANT]** Contains the exact `.pkl` model files used in the published paper. 
- `results_reproduced/`: An auto-generated folder. If you choose to re-train the models yourself, your new models will be saved here to avoid overwriting the original paper's models.

---

##  How to Use This Repository

We have structured the notebook to accommodate two main use cases: **Reproducing our paper's exact results** or **Training the models from scratch**.

### Option 1: Reproduce Exact Results from the Paper (Recommended)
If you want to generate the exact metrics, tables (Table 3 & 4), and spatial maps presented in the paper, you **do not** need to run the training process (Cell 2). 

1. Run **Cell 1**: Setup environment and load data.
2. *Skip Cell 2*.
3. Run **Cell 3 to Cell 6**: These cells are hard-coded to load the original `.pkl` files directly from the `pretrained_models/` folder. This guarantees 100% identical results to the publication.

### Option 2: Train Models from Scratch
If you want to understand our methodology or experiment with the PyCaret training pipeline:

1. Run **Cell 1**: Setup environment and load data (SMOTE applied with seed 1234).
2. Run **Cell 2**: This cell executes the PyCaret training process. 
   - *Note:* The newly trained models will be saved safely into the `results_reproduced/` directory. 
   - **Disclaimer:** Machine learning models trained on different local machines or cloud environments (with different hardware configurations, OS, or library versions) may yield slightly different performance metrics compared to our original publication, despite using fixed random seeds.

---

## Notebook Execution Breakdown

- **Cell 1:** Environment setup, data loading, and handling class imbalance via SMOTE.
- **Cell 2:** Demonstration of the PyCaret model training pipeline.
- **Cell 3:** Model evaluation using optimal threshold (Youden's J) using the pre-trained models.
- **Cell 4:** Frequency Ratio (FR) validation and automatic generation of Tables 3 and 4.
- **Cell 5:** Feature Importance visualization (Layer Cake Plot).
- **Cell 6:** Machine Learning Spatial Susceptibility Mapping (creates map comparison chunks).
- **Cell 7:** Frequency Ratio (FR) Spatial Mapping. 
