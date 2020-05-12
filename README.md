# tSNE implementation comparison

## Introduction

This guide compares performance of tSNE alogrithm on CPU platform vs GPU. For GPU, we are using Nvidia RAPIDSAI Framework.
In this example, rapidsai container was used with Singularity.

## Dataset

Dataset refered in this notebook can be found at; https://www.kaggle.com/roustekbio/breast-cancer-csv/data
All the missing values have been replaced with '0'

## Usage

```sh
ssh -L 8000:localhost:8000 muarif092@raad2-gfx.qatar.tamu.edu

srun --ntasks=18 --gres=gpu:v100:1 --time=08:00:00 --tunnel L8000:8000 --pty /bin/bash

module load cuda10.0

git clone https://github.com/mustafaarif/tSNE.git

cd tSNE/

mkdir data

# Download data from above mentioned source and place in data directory. This data contains few missing values. These values can be replaced with 0.

singularity shell /cm/shared/apps/rapidsai/rapids0.13-cuda10.0-centos7

source activate rapids

jupyter notebook --port 8000
```
## Conclusion

For breastCancer dataset, tSNE fit for CPU version took 2.89sec whereas GPU version took 0.89sec.
