如何在 Windows 系统上安装 PyTorch
=================================
- [如何在 Windows 系统上安装 PyTorch](#%e5%a6%82%e4%bd%95%e5%9c%a8-windows-%e7%b3%bb%e7%bb%9f%e4%b8%8a%e5%ae%89%e8%a3%85-pytorch)
  - [前提条件](#%e5%89%8d%e6%8f%90%e6%9d%a1%e4%bb%b6)
    - [Windows 系统](#windows-%e7%b3%bb%e7%bb%9f)
    - [Python](#python)
    - [软件包管理器](#%e8%bd%af%e4%bb%b6%e5%8c%85%e7%ae%a1%e7%90%86%e5%99%a8)
      - [Anaconda](#anaconda)
      - [pip](#pip)
  - [PyTorch 安装步骤](#pytorch-%e5%ae%89%e8%a3%85%e6%ad%a5%e9%aa%a4)
    - [使用 Anaconda 安装 PyTorch](#%e4%bd%bf%e7%94%a8-anaconda-%e5%ae%89%e8%a3%85-pytorch)
    - [使用 pip 安装 PyTorch](#%e4%bd%bf%e7%94%a8-pip-%e5%ae%89%e8%a3%85-pytorch)
  - [验证](#%e9%aa%8c%e8%af%81)
  
前提条件
--------

### Windows 系统

PyTorch 支持在以下 Window 系统上进行安装：

* Windows 7 及以上版本

  推荐 Windows 10 及以上版本。

* Windows Server 2008 r2 及以上版本

### Python

目前在 Windows 系统下安装 PyTorch 仅支持 Python 3.x 版本; Python 2.x 版本不支持。

由于 Windows 默认情况下并不安装 Python，您可以通过以下几种方式安装 Python：

* [Chocolatey](https://chocolatey.org/)
* [Python官方网站](https://www.python.org/downloads/windows/)
* [Anaconda](https://www.anaconda.com/distribution/#windows)

### 软件包管理器

安装 PyTorch binaries，需要使用软件包管理器。以下是 2 种支持的软件包管理器，您可以选择其中一种：

* Anaconda

  推荐使用 Anaconda，因为 Anaconda 提供了 PyTorch 的所有依赖关系，包括 Python 和 pip。

* pip 

#### Anaconda

使用支持 PyTorch 3.x 的 [64 位图形化安装程序](https://www.anaconda.com/distribution/#windows)，安装 Anaconda。点击安装程序链接，选择【运行】开始下载 Anaconda。下载完成后会自动弹出安装程序界面。选择默认方式进行安装即可。

#### pip

如果您已使用上述任一推荐方式安装了 Python，pip 将已经安装在了您的电脑上。

PyTorch 安装步骤
------------------

### 使用 Anaconda 安装 PyTorch

按照如下步骤，使用 Anaconda 安装 PyTorch。

1. 点击电脑左下端的【开始】，选择【Anaconda3】，点击【Anaconda Prompt】打开 Anaconda Prompt 界面。
2. 在 Ananconda Prompt 界面输入安装命令。 

   您可以根据您的需求，选择是否安装是否支持 CUDA 功能的 PyTorch。

   * 如果您的系统不支持 CUDA 的功能或者您不需要支持 CUDA 的功能，请输入以下命令：

         conda install pytorch torchvision cpuonly -c pytorch

   * 如果您的系统支持 CUDA 的功能，请根据需求输入命令：

     * 针对 CUDA 9.2： 
      
           conda install pytorch torchvision cudatoolkit=9.2 -c pytorch -c defaults -c numba/label/dev

     * 针对 CUDA 10.1

           conda install pytorch torchvision cudatoolkit=10.1 -c pytorch

  
   如果您在输入安装命令后，出现 HTTP 错误， 尝试重新输入运行安装的命令。 或者，您可以使用清华镜像。您可以按以下步骤使用清华镜像进行安装。

   a. 在 Anaconda Prompt 界面，输入以下命令：

          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/pkgs/free/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/pkgs/main/
          conda config --set show_channel_urls yes
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/pytorch/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/conda-forge/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/msys2/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/menpo/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/bioconda/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/peterjc123/
          conda config --add channels http://mirrors.tuna. tsinghua.edu.cn/anaconda/cloud/pytorch/
  
      注意：链接中是 `http`，不是 `https`。如果您不小心输入了 `https`，同样也会得到 HTTP 错误的报错。 

   b. 进入以下路径 ``C:\Users\<your user name>``，用任一文本编辑器打开 ``.condarc`` 文件， 删除 ``- defaults``所在代码行并保存更新后的文件。

   c. 在 Anaconda Prompt 界面，输入步骤 2 运行的命令并将 ``-c pytorch`` 从命令中删除。

### 使用 pip 安装 PyTorch




验证
-----

运行代码样例，验证 PyTorch 是否安装成功。如下提供的代码样例用于构建一个随机初始化的张量。

1. 在 Anaconda Prompt 界面，输入：

       python
  
2. 继续输入如下代码样例:

       from __future__ import print_function
       import torch
       x = torch.rand(5， 3)
       print(x)


正确的输出结果类似如下:

    tensor([[0.3380， 0.3845， 0.3217]，
            [0.8337， 0.9050， 0.2650]，
            [0.2979， 0.7141， 0.9069]，
            [0.1449， 0.1132， 0.1375]，
            [0.4675， 0.3947， 0.1426]])

      
     


