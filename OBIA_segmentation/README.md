# OBIA Solar Panel Segmentation (Phase 1)

This project demonstrates an **object-based image analysis (OBIA)** workflow for detecting solar panels from drone orthophotos using the open-source [NickySpatial](https://github.com/nickyspatial) library.  
It includes segmentation, feature/indices extraction, sample collection through a simple UI, and supervised classification.

---

# What this repo includes
- Jupyter notebook (`obia_solar_segmentation.ipynb`) with the workflow  
- A simple **web UI** (`index.html`, `main.js`) to pick training samples and export them as `samples.json`  
- Example outputs (segmented and classified GeoJSONs)  
- `environment.yaml` for easy environment setup with conda  

---

# Getting started

## 1. Setup environment
Using the provided conda environment file:

    conda env create -f environment.yaml
    conda activate obia

Or install manually (Python 3.9+ recommended):

    pip install nickyspatial
    pip install geopandas rasterio shapely fiona pyproj
    pip install scikit-learn numpy pandas tqdm jupyter

## 2. Run notebooks
Open the Jupyter notebook (`obia_solar_segmentation.ipynb`) and run the cells step by step.

This covers:
- Loading and (optionally) downsampling the orthophoto  
- Running segmentation with parameters such as `scale` and `compactness`  
- Adding custom indices (e.g., `(G - R) / (G + R)`)  
- Exporting segments to GeoJSON  

## 3. Collect training samples
- Open `webui/index.html` in a browser  
- Load the segment GeoJSON  
- Assign segments to classes (e.g., *Solar* / *Non-Solar*)  
- Download labeled samples as `samples.json`  

## 4. Classification
Train supervised models (Random Forest, SVM, KNN) using the labeled samples.  
- Random Forest generally performs best  
- KNN works moderately well  
- SVM may need more training samples to perform well  

Classified outputs are saved as GeoJSON files for visualization.  

---

# Results
- Segmentation and classification outputs are stored as GeoJSON files  
- Random Forest provides a good baseline for solar panel detection  
- Results improve with more and better-balanced training samples  
