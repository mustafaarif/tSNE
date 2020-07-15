# tSNE implementation comparison

## Introduction

This guide compares performance of tSNE alogrithm on CPU platform vs GPU. For GPU, we are using Nvidia RAPIDSAI Framework.
In this example, rapidsai container was used with Singularity.

## Dataset

Various datasets were used for this study.
Sources of datasets along with their usage guidelines is listed under 'datasets' directory

## Usage

```sh
# On your local machine, establish ssh connection to raad2 GPU cluster with Port Forwarding.
ssh -L 8000:localhost:8000 muarif092@raad2-gfx.qatar.tamu.edu

# Once you are logged into supercomputer, submit an interactive job to get hold of a GPU node
srun --ntasks=18 --gres=gpu:v100:1 --time=08:00:00 --tunnel L8000:8000 --pty /bin/bash

# Now load CUDA runtime
module load cuda10.0

# Clone the test code (needs to be done once)
git clone https://github.com/mustafaarif/tSNE.git

cd tSNE/

mkdir data

# Download data from above mentioned source and place in data directory.
# This data contains few missing values. These values can be replaced with 0.

# Start Container. We are using Nvidia provided RAPIDS container
singularity shell /cm/shared/apps/rapidsai/rapids0.13-cuda10.0-centos7

# Activate RAPIDS conda environment
source activate rapids

# Launch Jupyter notebook
jupyter notebook --port 8000
```
## Conclusion

For breastCancer dataset, tSNE fit for CPU version took 2.89sec whereas GPU version took 0.89sec.
