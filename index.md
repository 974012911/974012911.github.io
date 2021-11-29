## 菜鸟配置深度学习环境(Anaconda5.2+cuda10.2+Pytorch1.7)及遇到的问题

第一次记录。。

[toc]
### Anaconda 5.2 安装

在 https://repo.anaconda.com/ 选择 Anaconda-5.2.0-Windows-x86_64.exe

在Anaconda Prompt中输入以下命令，创建python3.6环境
```
conda create -n pytorch python=3.6
```
### Pytorch 1.7 安装

在安装过程中，尝试用官网的方法安装，发现速度太慢，遂放弃。

尝试用清华镜像源的方法安装，发现安装的是cpu版本的，torch.cuda.is_available()返回的是False，遂放弃。

最后整理看到的一种方法如下，可以成功解决问题。

在 https://download.pytorch.org/whl/torch_stable.html 选择对应的平台，注意这里的cuda版本

我选的是

`cu102/torchvision-0.6.0-cp36-cp36m-win_amd64.whl`，cuda 10.2版本，torchvision 0.6版本，python 3.6版本

`cu102/torch-1.7.0-cp36-cp36m-win_amd64.whl`，cuda 10.2版本，torch 1.7版本，python 3.6版本

把下载好的文件复制到Anaconda的位置`Anaconda\pkgs`下。

在`Anaconda Prompt`中运行下面命令，安装上面两个文件。

```
pip install 文件名
pip install 文件名
```

安装后`torch.cuda.is_available()=True`




### CUDA 10.2 安装

在 https://developer.nvidia.com/cuda-toolkit-archive 选择'CUDA Toolkit 10.2'，进入选择对应的系统平台，下载

![image](https://user-images.githubusercontent.com/67214810/143830499-003160ab-49ff-465c-87e7-72aaf96bef19.png)

安装过程我都设为默认的，一直点下一步

### Jupyter 配置

在`Anaconda Prompt`中`pytorch`下运行

```
conda install nb_conda_kernels
```

安装Jupyter所需配置


### 配置好torch环境，在Pycharm里import torch报错
#### 报错内容：import torch
```
Please note and check the following:

  * The Python version is: Python3.7 from "D:\anaconda\envs\qr_env\python.exe"
  * The NumPy version is: "1.19.1"

and make sure that they are the versions you expect.
Please carefully study the documentation linked above for further help.

Original error was: DLL load failed: 找不到指定的模块。
```
由于是通过Anaconda创建自己的环境，并且安装torch等包，在`Anaconda prompt`命令窗口下是可以正常导入的，而在pycharm编译器中报错。
因此需要在pycharm创建的新环境中添加环境变量，即在Anaconda环境下有支持import torch的dll
#### 解决方法——添加环境变量

在Pycharm中`Run->Edit Configurations...->“文件名”->Environment variables`添加相关路径，仅供参考

添加后重新打开Pycharm（我重开了之后`import torch`成功）

![image](https://user-images.githubusercontent.com/67214810/143827663-7a038f41-10c5-429f-a5a9-0dcf5378b28d.png)

