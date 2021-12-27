# deeplearning-pytorch
This repo is created to document my learning!
## Start up with ubuntu apt
First, we have to set up the invironment. The following is what I used.
- Operating system: Linux, apt: ubuntu 18.04
- Graphic card: GTX 1080
- Nvidia driver: can be the latest
- CUDA: any version that compatiable with nvidia driver. (Recommend >= 10.1) I used 10.2
- Cudnn: the latest update that compatible with CUDA 10.2

# Install Nividia driver
Check your graphic card model.
```python
lshw -c video
```
Go [here](https://www.nvidia.com/Download/index.aspx), input your information and download. Then
```
$ chmod +x NVIDIA-Linux-x86_64-418.56.run
