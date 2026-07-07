# Data Science for Maritime Transportation

This repository provides the teaching code and example datasets for **Data Science for Maritime Transportation**. The code is organized by book chapter and is intended to help readers reproduce the demonstrations, understand the modeling workflow, and adapt the examples to their own maritime data-analysis tasks.

The examples are mainly provided as Jupyter notebooks. They cover common data-science tasks in maritime transportation, including AIS data processing, trajectory analysis, clustering, prediction, anomaly detection, propulsion-power estimation, ocean-wave modeling, graph-based traffic-flow forecasting, and ETA prediction.

## 1. Repository Structure

```text
Data-Science-for-Maritime-Transportation/
├── Chapter_1/
│   └── Chapter_1.ipynb
├── Chapter_2/
│   └── Chapter_2.ipynb
├── Chapter_3/
│   └── Chapter_3.ipynb
├── Chapter_5/
│   └── Chapter_5.ipynb
├── Chapter_6/
│   └── Chapter_6.ipynb
├── Chapter_7/
│   └── Chapter_7.ipynb
├── Chapter_8/
│   ├── Chapter_8.ipynb
│   ├── AIS_train.csv
│   └── AIS_test.csv
├── Chapter_9/
│   ├── Chapter_9.ipynb
│   └── ais_with_era5_cmems_final.csv
├── Chapter_10/
│   └── Chapter_10.ipynb
├── Chapter_11/
│   ├── Chapter_11.ipynb
│   └── GNN_flow_data/
├── Chapter_12/
│   ├── Chapter_12.ipynb
│   └── ETA_data.csv
├── data/
│   ├── AIS_data.csv
│   ├── AIS_resampled_5min.csv
│   └── cmems_obs-wind_glo_phy_my_l4_0.125deg_PT1H_1763738218046.nc
├── requirements.txt
└── README.md
```

Each `Chapter_X` folder contains the notebook and, where necessary, chapter-specific data files. The `data` folder stores shared datasets used by multiple examples.

## 2. Recommended Environment

The recommended Python version is:

```bash
Python 3.10
```

Python 3.10 is recommended because it provides good compatibility with the scientific-computing, machine-learning, geospatial, and deep-learning packages used in the notebooks.

## 3. Environment Configuration

### Option A: Using Conda

This is the recommended method, especially if you use Windows or need geospatial packages such as `cartopy`, `shapely`, `pyproj`, `xarray`, and `netCDF4`.

```bash
conda create -n maritime-ds python=3.10 -y
conda activate maritime-ds
```

Install geospatial and scientific dependencies first:

```bash
conda install -c conda-forge cartopy shapely pyproj xarray netCDF4 h5py zarr dask -y
```

Then install the remaining dependencies:

```bash
pip install -r requirements.txt
```

Register the environment as a Jupyter kernel:

```bash
python -m ipykernel install --user --name maritime-ds --display-name "Python (maritime-ds)"
```

Start JupyterLab:

```bash
jupyter lab
```

Then select the kernel named **Python (maritime-ds)** when running the notebooks.

### Option B: Using venv and pip

If you prefer a lightweight virtual environment, you can use `venv`.

For Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python -m ipykernel install --user --name maritime-ds --display-name "Python (maritime-ds)"
jupyter lab
```

For macOS or Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python -m ipykernel install --user --name maritime-ds --display-name "Python (maritime-ds)"
jupyter lab
```

If installation of `cartopy` or other geospatial packages fails under pip, use the Conda method instead.

## 4. Required Packages

The main dependencies include:

- `numpy`, `pandas`, `scipy`, `openpyxl` for numerical computing and data processing;
- `matplotlib`, `seaborn`, `pillow` for visualization;
- `scikit-learn`, `torch`, `stable-baselines3`, `gymnasium` for machine learning, deep learning, and reinforcement learning examples;
- `xarray`, `netCDF4`, `h5py`, `zarr`, `dask`, `pyarrow` for gridded oceanographic and large-scale data processing;
- `cartopy`, `shapely`, `pyproj`, `copernicusmarine` for geospatial and ocean-data analysis;
- `networkx`, `fastdtw`, `tqdm`, `requests`, `joblib` for graph modeling, trajectory similarity, utilities, and parallel processing.

The full dependency list is provided in:

```text
requirements.txt
```

## 5. Running the Notebooks

After configuring the environment, open JupyterLab from the project root:

```bash
cd Data-Science-for-Maritime-Transportation
jupyter lab
```

Open the notebook of the corresponding chapter, for example:

```text
Chapter_8/Chapter_8.ipynb
```

Run the notebook cells sequentially from top to bottom. Some notebooks read local data files using relative paths. Therefore, it is recommended to keep the original folder structure unchanged.

## 6. Data Notes

The repository contains both shared and chapter-specific data files.

Shared data are stored in:

```text
data/
```

Chapter-specific data are stored inside the corresponding chapter folders, for example:

```text
Chapter_8/AIS_train.csv
Chapter_8/AIS_test.csv
Chapter_12/ETA_data.csv
```

Some datasets are relatively large, especially AIS and NetCDF files. If a notebook runs slowly, check memory usage and consider running the notebook on a machine with sufficient RAM.

## 7. Reproducibility Notes

The notebooks are designed for teaching and demonstration purposes. Results may vary slightly across machines because of differences in package versions, random initialization, hardware, and numerical backends.

For more stable results, readers may:

1. use the recommended Python version;
2. install packages from `requirements.txt`;
3. keep the original directory structure;
4. run all cells sequentially;
5. set random seeds when modifying model-training code.

## 8. Common Issues

### 8.1 `ModuleNotFoundError`

Make sure that the correct Jupyter kernel is selected. The recommended kernel name is:

```text
Python (maritime-ds)
```

If the problem remains, reinstall dependencies:

```bash
pip install -r requirements.txt
```

### 8.2 `cartopy` Installation Fails

This is common on Windows. Use Conda instead:

```bash
conda install -c conda-forge cartopy shapely pyproj
```

### 8.3 PyTorch Installation Issues

If `torch` cannot be installed properly, install it separately according to your operating system, Python version, and CUDA version. For CPU-only execution, the standard pip installation is usually sufficient.

### 8.4 Large Data Files Load Slowly

Some AIS and NetCDF examples require relatively large files. If loading is slow, close other memory-intensive programs or run the notebook on a machine with more available RAM.

## 9. Suggested Workflow for Readers

A typical workflow is:

1. create a clean Python environment;
2. install dependencies using `requirements.txt`;
3. start JupyterLab from the project root;
4. open the notebook for the target chapter;
5. run cells sequentially;
6. modify parameters or replace the example data with your own data.

## 10. Notes for Using Your Own Data

When replacing the example data, make sure that:

- column names match those expected by the notebook;
- time columns are correctly parsed as datetime variables;
- coordinate columns use consistent units and coordinate systems;
- missing values are handled before model training;
- train-test splits are adjusted according to the new dataset size.

## 11. Citation

If you use this repository for teaching, research, or derivative work, please cite the corresponding book or chapter associated with this code repository.

## 12. License

No license file is included in the current repository. Please contact the author before redistributing, modifying, or using the code for commercial purposes.
