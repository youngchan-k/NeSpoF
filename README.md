# Neural Spectro-polarimetric Fields (NeSpoF)
[NeSpoF](https://youngchan-k.github.io/NeSpoF) (Neural Spectro-polarimetric Field) is a physically valid neural representation for spectro-polarimetric fields. It represents Stokes vectors and volumetric density as functions of position, viewing direction, and wavelength.
The code is based on [NeRF-pytorch](https://github.com/yenchenlin/nerf-pytorch).

<img src='NeSpoF.PNG'/>

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

## Project structure
- `run_nespof.py` — main entry for training and rendering
- `core/` — training helpers (network, losses, ray utilities)
- `data/` — data loaders (`load_synthetic.py`, `load_real.py`)
- `visualization/` — Stokes and polarimetric visualization
- `utils/` — preprocessing scripts, pose estimation (COLMAP), Stokes utilities, camera frustum tools
- `notebooks/` — Jupyter notebooks (color mapping, func fitting, etc.)
- `configs/` — config files for synthetic, real, and video runs
- `scripts/` — shell scripts for batch preprocessing

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

## Usage
To train NeSpoF on synthetic datasets:
```bash
python run_nespof.py --config configs/synthetic/{DATASET}.txt
```
Replace `{DATASET}` with `ajar`, `cbox_dragon`, `cbox_sphere`, or `hotdog`.

---

To train NeSpoF on real-world datasets:
```bash
python run_nespof.py --config configs/real/{DATASET}.txt
```
Replace `{DATASET}` with `scene_1`, `scene_2`, `scene_3`, or `scene_4`.

---

After training, you can also render the video for Stokes vector and polarimetric visualization:
```bash
python run_nespof.py --config configs/video/{DATASET}.txt
```
Replace `{DATASET}` with `ajar`, `cbox_dragon`, `cbox_sphere`, `hotdog`, `scene_1`, `scene_2`, `scene_3`, or `scene_4`.


## Citation

```bibtex
@article{kim2023neural,
  title={Neural Spectro-polarimetric Fields},
  author={Kim, Youngchan and Jin, Wonjoon and Cho, Sunghyun and Baek, Seung-Hwan},
  journal={arXiv preprint arXiv:2306.12562},
  year={2023}
}
```
