# deeplearning-pytorch
This repo is created to document my learning!
## Start up with ubuntu apt
First, we have to set up the invironment. The following is what I used.
- Operating system: Linux, apt: ubuntu 18.04
- Graphic card: GTX 1080
- Nvidia driver: can be the latest
- CUDA: any version that compatiable with nvidia driver. (Recommend >= 10.1) I used 10.2
- Cudnn: the latest update that compatible with CUDA 10.2

### Install Nividia driver
Check your graphic card model.
```
$ lshw -c video
```
Go [here](https://www.nvidia.com/Download/index.aspx), input your information and download. Then
```
$ chmod +x filename
$ sudo ./filename
$ sudo reboot now
```
Check your installation
```
$ nvidia-smi
```
### Install CUDA 10.2
Go [here](https://developer.nvidia.com/cuda-downloads), and download CUDA 10.2 and then choose, Linux >> x86_64 >> Ubuntu >> 18.04 >> deb(local). Then run the command that u see in the base installer.
### Install CUDNN
Go to this [link](https://developer.nvidia.com/cudnn) to download CUDNN that compatible with CUDA 10.2 and then run the following command.
```
$ tar -xzvf filename
$ sudo cp cuda/include/cudnn*.h /usr/local/cuda-10.2/include
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda-10.2/lib64
$ sudo chmod a+r /usr/local/cuda-10.2/include/cudnn*.h /usr/local/cuda-10.2/lib64/libcudnn*
$ gedit ~/.bashrc
```
paste this and save
```
export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}"
```
