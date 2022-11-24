
#!/bin/bash

#### steps 

verify the system has a cuda-capable gpu

download and install the nvidia cuda toolkit and cudnn

setup environmental variables

verify the installation


#### to verify your gpu is cuda enable check
```
lspci | grep -i nvidia
```

#### If you have previous installation remove it first. 
```
sudo apt-get purge nvidia*
sudo apt remove nvidia-*
sudo rm /etc/apt/sources.list.d/cuda*
sudo apt-get autoremove && sudo apt-get autoclean
sudo rm -rf /usr/local/cuda*
```
#### system update
```
sudo apt-get update
sudo apt-get upgrade
```

#### install other import packages
```
sudo apt-get install g++ freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libglu1-mesa libglu1-mesa-dev
```

#### first get the PPA repository driver
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```

#### install nvidia driver with dependencies
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.7.0/local_installers/cuda-repo-ubuntu2004-11-7-local_11.7.0-515.43.04-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-11-7-local_11.7.0-515.43.04-1_amd64.deb
#if error happend 
sudo cp /var/cuda-repo-ubuntu2004-11-7-local/**** usr/share/keyrings/cuda-archive-keyring.gpg
sudo cp /var/cuda-repo-ubuntu2004-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
```

#### installing CUDA-11.7
 ```
sudo apt install cuda-11-7 
```
#### setup your paths
```
echo 'export PATH=/usr/local/cuda-11.7/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-11.7/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
sudo ldconfig
```

#### install cuDNN v11.7

[Download libcudnn8-dev_8.5.0.96-1+cuda11.7_amd64.deb and libcudnn8_8.5.0.96-1+cuda11.7_amd64.deb]{https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/}
```
wget ....
sudo dpkg -i libcudnn8-dev_8.5.0.96-1+cuda11.7_amd64.deb
sudo dpkg -i libcudnn8_8.5.0.96-1+cuda11.7_amd64.deb
```
https://medium.com/geekculture/installing-cudnn-and-cuda-toolkit-on-ubuntu-20-04-for-machine-learning-tasks-f41985fcf9b2

#### Finally, to verify the installation, check
```
nvidia-smi
nvcc -V
```
#### install Pytorch (an open source machine learning framework)
