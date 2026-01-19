# PH-DETR

**Official implementation** of  *"PH-DETR"* .

##  ⚙️Installation
We use  `python=3.10,pytorch=2.0.1,cuda=11.7`. Other versions may also be available. Clone the repository locally and install with
```
git clone https://github.com/lei12879/PH-DETR.git
cd PH-DETR/PH-DETR
```
## ⚙️Example conda environment setup

### 1. Create environment
```
conda create --name ph_detr python=3.10 -y
conda activate ph_detr
```
### 2. Install pytorch [Previous PyTorch Versions | PyTorch](https://pytorch.org/get-started/previous-versions/)
```
conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.7 -c pytorch -c nvidia
```

### 3. Other needed packages
```
pip install -r requirements.txt
```

##  📂Dataset Preparation


###     Download and extract [VisDrone2019](https://github.com/VisDrone/VisDrone-Dataset.git)  train and val images. 
```
path/to/visdrone/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```

You can modify config [`img_folder`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/visdrone_detection.yml)[`ann_file`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/visdrone_detection.yml)

### Download and extract [HazyDet](https://github.com/GrokCV/HazyDet) train and val images. 
```
path/to/HazyDet/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```
You can modify config [`img_folder`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/hzdet_detection.yml)[`ann_file`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/hzdet_detection.yml)

###   Download and extract [DroneVehicle](https://github.com/VisDrone/DroneVehicle) train and val images. 
```
path/to/HazyDet/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```
You can modify config [`img_folder`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/dronevehicle_detection.yml)[`ann_file`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/dronevehicle_detection.yml)

### Download and extract [TinyPerson](https://universe.roboflow.com/chris-d-dbyby/tinyperson)  train and val images. 
```
path/to/tinyperson/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```
You can modify config [`img_folder`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/tinyperson_detection.yml)[`ann_file`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/tinyperson_detection.yml)


### Download and extract [Cityscapes](https://www.cityscapes-dataset.com/) train and val images. 
```
path/to/tinyperson/
  annotations/  # annotation json files
  train/    # train images
  val/      # val images
```
You can modify config [`img_folder`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/cityscapes_detection.yml)[`ann_file`](https://github.com/lei12879/PAE-DETR/blob/main/configs/dataset/cityscapes_detection.yml)


## 🏋️ Training & Testing

### Single-GPU Training
```bash
# VisDrone 
python train.py -c configs/phdetr/PHDETR_visdrone.yml

# HazyDet
python train.py -c configs/phdetr/PHDETR_hzdet.yml

# DroneVehicle
python train.py -c configs/phdetr/PHDETR_dronevehicle.yml

# TinyPerson 
python tools/train.py -c configs/phdetr/PHDETR_tinyperson.yml

# Cityscapes
python train.py -c configs/phdetr/PHDETR_cityscape.yml
```

### Multi-GPU Distributed Training

```bash
# 4 GPUs example
python -m torch.distributed.launch --nproc_per_node=4 \
    train.py -c configs/phdetr/PHDETR_visdrone.yml 
```
### Testing
```bash
python train.py -c path/to/config -r path/to/checkpoint --test-only
```
