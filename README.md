# YOLOv7 Surface Defect Detection Project

This repository contains the setup and training process for the YOLOv7 model to detect surface defects. Follow the instructions below to set up and run the project.

---

## Prerequisites
- Python 3.8
- GPU with CUDA support (optional but recommended for training)

---

## Setup Instructions

### 0. Create a Python Environment
Create a new Python environment named `yolov7` with Python version 3.8:
```bash
conda create -n yolov7 python=3.8 -y
conda activate yolov7
```

---

### 1. Initialize YOLOv7 Submodule
Clone and install the YOLOv7 submodule:
```bash
git submodule init
git submodule update yolov7
cd yolov7
pip install -r requirements.txt
```

---

### 2. Download the YOLOv7 Model
Download the pre-trained YOLOv7 model:
```bash
mkdir models/
cd models/
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
cd ..
```

---

### 3. Setup the Dataset
Prepare the dataset for training:
```bash
mkdir data/
unzip raw_data/neu-et.zip -d data/
```

---

### 4. Train the Model
Start training the YOLOv7 model. Use either of the following methods:

#### Option 1: Run the shell script
```bash
bash train.sh
```

#### Option 2: Run the training script directly
```bash
python yolov7/train.py --weights models/yolov7.pt --data data/neu-det/data.yaml --cfg yolov7/cfg/training/yolov7.yaml --epochs 50 --batch-size 16 --device 0
```

---

## Notes
- Ensure `raw_data/neu-et.zip` exists in the root directory before starting.
- Modify the training parameters in the `train.sh` file or command as needed.

---

## Project Structure
```plaintext
.
├── data/
│   └── neu-det/
├── models/
│   └── yolov7.pt
├── raw_data/
│   └── neu-et.zip
├── yolov7/
│   ├── train.py
│   └── cfg/
│       └── training/
│           └── yolov7.yaml
└── train.sh
```
