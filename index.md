## 菜鸟配置深度学习环境(Anaconda5.2+cuda10.2+Pytorch1.10)及遇到的问题

第一次记录。。

[toc]
### Anaconda 5.2 安装

在 https://repo.anaconda.com/ 选择 Anaconda-5.2.0-Windows-x86_64.exe

在Anaconda Prompt中输入以下命令，创建python3.6环境
```
conda create -n pytorch python=3.6
```
### Pytorch 1.10 安装

在 `https://pytorch.org/` 选择对应的平台，注意这里的cuda版本

![image](https://user-images.githubusercontent.com/67214810/143828919-09202ccf-caf6-4870-ba91-44aecee5390a.png)

在`Anaconda Prompt`中输入以下命令，创建python3.6环境
```
conda create -n pytorch python=3.6
```




### CUDA 10.2 安装

在 `https://developer.nvidia.com/cuda-toolkit-archive` 选择'CUDA Toolkit 10.2'，进入选择对应的系统平台，下载

![image](https://user-images.githubusercontent.com/67214810/143830499-003160ab-49ff-465c-87e7-72aaf96bef19.png)

安装过程我都设为默认的，一直点下一步




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

