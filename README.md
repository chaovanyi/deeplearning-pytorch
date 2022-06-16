# deeplearning-pytorch
This repo is created to document my learning!
## Start up with ubuntu apt
First, we have to set up the environment. The following is what I used.
- Operating system: Linux, apt: ubuntu 18.04
- Graphic card: GTX 1080 (edit: now I use RTX A4500)
- Nvidia driver: can be the latest
- CUDA: any version that compatiable with nvidia driver. (Recommend >= 10.1) I used 10.2 (edit: there are some problem when I used 10.2 with my new gpu. Now I used 11.4.4)
- Cudnn: the latest update that compatible with CUDA 10.2

### Install Nividia driver

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install nvidia-driver-470
$ sudo reboot now
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
### Install anaconda
Download anaconda from [here](https://www.anaconda.com/products/individual#linux) and the run the following command
```
$ sha256sum filename
$ bash filename
```
If you use conda init and want to deactivate it, run the following command
```
$ conda config --set auto_activate_base False
```
If there is a problem with permission, run the following command
```
$ sudo chmod 777 -R ~/anaconda3/
$ sudo chmod 777 -R ~/.conda/
```
Create deeplearning environment in anaconda
```
$ conda create --name deeplearning python=3.7
```
Activate the environment, install pytorch and other useful library
```
$ conda activate deeplearning
$ conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
$ pip install pandas numpy matplotlib opencv-python tqdm tb-nightly
$ pip install -U scikit-learn
```
### Install IDE
For editor, I used Pycharm.
```
$ sudo snap install pycharm-community --classic
```
Run pycharm. After creating project, go to file => setting => on Project: 'name', select Python Interpreter => on setting logo, select Add... => Select conda environment => select Existing environment => (you should see deeplearning environment that we've just created)

Fix cv2 and pyqt
```
import os, sys
ci_build_and_not_headless = False
try:
    from cv2.version import ci_build, headless
    ci_and_not_headless = ci_build and not headless
except:
    pass
if sys.platform.startswith("linux") and ci_and_not_headless:
    os.environ.pop("QT_QPA_PLATFORM_PLUGIN_PATH")
if sys.platform.startswith("linux") and ci_and_not_headless:
    os.environ.pop("QT_QPA_FONTDIR")
```
Or using headless version
```
pip install opencv-python-headless
```
