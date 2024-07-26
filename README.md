# setup_your_server

This guide will assist you in quickly setting up a Linux server for deep learning tasks.

Suppose you have a new server (for instance, an AWS machine) and you aim to run deep learning experiments. The first steps involve installing CUDA and setting up an Anaconda environment. This script simplifies the process! Just follow the commands provided, and you'll be ready to go.

Execute the following commands in your terminal, one line at a time.

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
wget https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
bash Anaconda3-2024.06-1-Linux-x86_64.sh -b
export PATH=~/anaconda3/bin:$PATH
source ~/.bashrc
conda update -n base -c defaults conda
conda init

# re-open shell
```

## Step 3: Create a Conda environment

```
# Create a new Conda environment with Python 3.9
conda create -n deeplearning python=3.9 -y
conda activate deeplearning

# Install PyTorch with CUDA support
conda install pytorch torchvision torchaudio pytorch-cuda -c pytorch -c nvidia
pip install tqdm opencv-python matplotlib h5py wandb lpips scikit-image

# Verify PyTorch installation
python -c "import torch; print(torch.cuda.is_available())"
```
