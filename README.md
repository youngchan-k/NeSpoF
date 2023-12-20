# Neural Spectro-polarimetric Fields (NeSpoF)
[NeSpoF](https://youngchan-k.github.io/nespof) (Neural Spectro-polarimetric Field) is a physically-valid neural representation that models spectro-polarimetric fields.
The code is based on [NeRF-pytorch](https://github.com/yenchenlin/nerf-pytorch) and you should follow the [requirements.txt](https://github.com/yenchenlin/nerf-pytorch/blob/master/requirements.txt) provided there. For more details, please check our project website [here](https://youngchan-k.github.io/nespof)

## Installation
```
git clone https://github.com/youngchan-k/NeSpoF.git
cd nespof
pip install -r requirements.txt
pip install imath
conda install -c conda-forge openexr
(or conda install -c conda-forge openexr-python)
```

## Datasets
Download the data [here](http://cgdata.postech.ac.kr/sharing/fkMLq3LSK). Place the downloaded dataset according to the following directory structure:

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

## How To Run?
To train NeSpoF on synthetic datasets:
```
python run_nespof.py --config configs/synthetic/{DATASET}.txt
```
replace {DATASET} with ajar | cbox_dragon | cbox_sphere | hotdog.

---

To train NeSpoF on real-world datasets:
```
python run_nespof.py --config configs/real/{DATASET}.txt
```
replace {DATASET} with scene_1 | scene_2 | scene_3 | scene_4.

---

After training, you can also render the video for Stokes vector and polarimetric visualization:
```
python run_nespof.py --config configs/video/{DATASET}.txt
```
replace {DATASET} with ajar | cbox_dragon | cbox_sphere | hotdog | scene_1 | scene_2 | scene_3 | scene_4.
