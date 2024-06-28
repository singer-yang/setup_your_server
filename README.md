# setup_your_server

This code can help you fast setup a linux server for deep learning, for example, an AWS machine.

Think about you got a new server (for exampl, a AWS machine) and you want to run deep learning experiments. You will first need to install cuda and create an anaconda enviroment. This script will help you make things easier! Just follow the command and you will settle up!

Execute the following commands in your terminal line by line.

## Step 1: Install NVIDIA CUDA Drivers

```
# Update and Upgrade the System
sudo apt-get update
sudo apt-get upgrade -y

# Install NVIDIA CUDA Drivers
# Using the latest production branch version as of the last update
sudo apt-get install nvidia-driver-535
sudo apt install nvidia-cuda-toolkit
sudo reboot

# After reboot, verify the installation
nvidia-smi
```

## Step 2: Install Anaconda

```
# Using the latest installer for Linux (64-bit) as of the last update
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
bash Anaconda3-2023.09-0-Linux-x86_64.sh -b
export PATH=~/anaconda3/bin:$PATH
source ~/.bashrc
conda update -n base -c defaults conda
conda init

# re-open shell
```

## Step 3: Create a Conda environment and install packages

```
# Create a new Conda environment with Python 3.9
conda create -n diffgwg python=3.9 -y
conda activate diffgwg

# Install PyTorch with CUDA support
conda install pytorch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 pytorch-cuda=12.1 -c pytorch -c nvidia
pip install tqdm opencv-python matplotlib h5py wandb

# Verify PyTorch installation
python -c "import torch; print(torch.cuda.is_available())"
```
