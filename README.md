# Neural Spectro-polarimetric Fields (NeSpoF)

[NeSpoF](https://youngchan-k.github.io/NeSpoF) (Neural Spectro-polarimetric Field) is a physically valid neural representation for spectro-polarimetric fields. It represents Stokes vectors and volumetric density as functions of position, viewing direction, and wavelength.

The code is based on [NeRF-pytorch](https://github.com/yenchenlin/nerf-pytorch).

<img src="NeSpoF.PNG"/>

## Installation

```bash
git clone https://github.com/youngchan-k/NeSpoF.git
cd NeSpoF
pip install -r requirements.txt
```

Install OpenEXR dependencies for EXR I/O:

```bash
pip install imath
conda install -c conda-forge openexr
# or:
conda install -c conda-forge openexr-python
```

## Project Structure

| Path | Description |
|---|---|
| `run_nespof.py` | Main entry point for training and rendering |
| `core/` | Training utilities, network definitions, losses, and ray helpers |
| `data/` | Dataset loaders for synthetic and real-world data |
| `visualization/` | Stokes and polarimetric visualization tools |
| `utils/` | Preprocessing utilities, COLMAP pose estimation, and helper functions |
| `notebooks/` | Jupyter notebooks for analysis and visualization |
| `configs/` | Configuration files for training and rendering |

Run all commands from the project root (e.g. `python run_nespof.py ...`, `python utils/data_preprocess_real.py ...`).

## Datasets

Download the dataset [here](https://drive.google.com/drive/folders/1W7apuXPA3EkyUs8VgZgwdMpnc96aLXXJ). Synthetic data can also be generated using the [Mitsuba 3 rendering pipeline](https://github.com/youngchan-k/NeSpoF_mitsuba_rendering). Place the downloaded dataset according to the following directory structure:

```
data
|-- synthetic
|   |-- ajar
|   |-- cbox_dragon
|   |-- ...
|-- real
    |-- scene_1
    |-- scene_2
    |-- ...
```

## Preprocessing
⚠️ Not necessary if you use the downloaded dataset

Preprocessing utilities are located in `utils/`:

```bash
# Preprocess synthetic data
python utils/data_preprocess_synthetic.py

# Preprocess real-world data
python utils/data_preprocess_real.py
```

Real-world preprocessing uses the COLMAP helpers under `utils/poses/`. Make sure COLMAP is installed and available from your command line before running pose estimation.

## Usage

Run NeSpoF with:

```bash
python run_nespof.py --config configs/{TYPE}/{DATASET}.txt
```

### Available config types

| Type | Description | Datasets |
|---|---|---|
| `synthetic` | Train on synthetic datasets | `ajar`, `cbox_dragon`, `cbox_sphere`, `hotdog` |
| `real` | Train on real-world datasets | `scene_1`, `scene_2`, `scene_3`, `scene_4` |
| `video` | Render Stokes/polarimetric visualization videos | All datasets above |

Example:

```bash
# Train on a synthetic dataset
python run_nespof.py --config configs/synthetic/ajar.txt

# Train on a real-world dataset
python run_nespof.py --config configs/real/scene_1.txt

# Render visualization videos
python run_nespof.py --config configs/video/ajar.txt
```

## Citation

```bibtex
@article{kim2023neural,
  title={Neural Spectro-polarimetric Fields},
  author={Kim, Youngchan and Jin, Wonjoon and Cho, Sunghyun and Baek, Seung-Hwan},
  journal={arXiv preprint arXiv:2306.12562},
  year={2023}
}
```
