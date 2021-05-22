AdaLab: Diversifying Dialog Generation via Adaptive Label Smoothing

pytorch implementation

This repo is tested on Ubuntu 16.04, and codes are based on a modified version of [OpenNMT-py](https://github.com/OpenNMT/OpenNMT-py).

| Table of Contents |
|-|
| [Setup](#setup)|
| [Training](#training)|
| [Evaluation](#evaluation)|



## Setup

### Dependencies

Install other dependecies:
```bash
conda create -n adalab python=3.7.4
conda activate adalab
conda install pytorch==1.7.1 torchvision torchaudio cudatoolkit=10.1 -c pytorch -n adalab 

pip install -r requirement.txt
mkdir checkpoint
mkdir log_dir
mkdir result
```



## Training

### Data preprocess
A script(`scripts/preprocess.sh`) performs preprocess data.

Please download the `data.zip`  and unzip it. Put the `data_daily` in the root dir.

DailyDialog dataset will be preprocessed via OpenNMT library  in ```script/preprocess.sh``` .

```bash
bash scripts/preprocess.sh
```


### Training 

We trianing our model using TITAN  Xp  12GB gpu in single.

```bash
bash scripts/train.sh
```

The best checkpoint will be reported in training log.

### Inference

A script (`scripts/inference.sh`) performs generation.
Please specify `GPUID` and `MODEL`(path).

```bash
bash scripts/inference.sh GPUID MODEL
```

The generated file will be saved in `result` dir



## Evaluation


### Evaluation

A script (`scripts/eval.py`) performs evaulation at 4 metrics

Please specify the absolute directory of this project at ```DIRPATH``` and generated file at ```PATH```

```bash
python script/eval.py DIRPATH PATH
```

