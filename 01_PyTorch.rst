Installing PyTorch on Windows
=============================

Prerequisites
--------------

* :ref:`win_distr`
* :ref:`sec_python`
* :ref:`package_manager`


.. _win_distr:

Supported Windows Distributions
+++++++++++++++++++++++++++++++

PyTorch is supported on the following Windows distributions:

* Windows 7 and greater

  Windows 10 or greater is recommended.

* Windows Server 2008 r2 and greater

.. _sec_python:

Python
++++++

Currently, PyTorch on Windows only supports Python 3.x; Python 2.x is not supported.

As Python is not installed by default on Windows, there are multiple ways to install Python:

* `Chocolatey <https://chocolatey.org/>`_
* `Python website <https://www.python.org/downloads/windows/>`_
* `Anaconda <https://www.anaconda.com/distribution/#windows>`_

.. _package_manager:

Package Manager
++++++++++++++++

To install the PyTorch binaries, use at least one of the following two supported package managers:

* :ref:`Anaconda1`

* :ref:`pip` 


..  _Anaconda1:

Anaconda
````````

Anaconda is the recommended package manager,  because it provides all of the PyTorch dependencies in one, sandboxed install, including Python and pip.

To install Anaconda, use the `64-bit graphical installer <https://www.anaconda.com/distribution/#windows>`_ for PyTorch 3.x. Click the installer link and select Run. Anaconda will be downloaded and the installer prompt will be presented to you. The default options are generally sane.

..  _pip:

pip
````

If you installed Python by any of the recommended ways mentioned in :ref:`sec_python`, pip will have already been installed for you.

Installing PyTorch
------------------

Installing PyTorch through Anaconda
+++++++++++++++++++++++++++++++++++

To install PyTorch with Anaconda, follow these steps:

1. Open an Anaconda prompt via Start | Anaconda3 | Anaconda Prompt.
#. Run the command to install the desired PyTorch. 

   * If you do not have a CUDA-capable system or do not require CUDA, run the following command:
    
     .. code-block:: c
    
        conda install pytorch torchvision cpuonly -c pytorch

   * If you have a CUDA-capable system, choose to run the command that suits you:

     * For CUDA 9.2: 
      
       .. code-block:: c

          conda install pytorch torchvision cudatoolkit=9.2 -c pytorch -c defaults -c numba/label/dev

     * For CUDA 10.1

       .. code-block:: c      

          conda install pytorch torchvision cudatoolkit=10.1 -c pytorch

   .. _fig_error:
   
   .. figure:: figs/HTTPError.*
      :scale: 30%
      :align: center
   
      Example of HTTP Error
   
   If you get an HTTP error like shown in :numref:`fig_error`, you may retry running the command. Optionally, use Tsinghua Tuna mirrors by following these steps: 

   a. In the Anaconda Prompt, run the following commands:

      .. code-block:: c
      
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
         conda config --set show_channel_urls yes
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/peterjc123/
         conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
  
      .. Note:: Pay attention to ``http``. If you mistakenly type ``https``, HTTP errors occur, too.

   #. Go to ``C:\Users\<your user name>``, open the ``.condarc`` file with a text editor, remove the ``- defaults`` line, and save the file.

   #. In the Anaconda Prompt, run the command in Step 2 but remember to remove ``-c pytorch`` from the command line.

Installing PyTorch through Pip
+++++++++++++++++++++++++++++++++++


Verifying Installation
-----------------------

To verify that you have successfully installed the desired PyTorch, run sample PyTorch code to construct a randomly initialized tensor.

1. In the Anaconda Prompt, type:

   .. code-block:: c

      python
  
#. Enter the following code:

   .. code-block:: c 

      from __future__ import print_function
      import torch
      x = torch.rand(5, 3)
      print(x)


The output is shown in :numref:`fig_tensor`.

.. _fig_tensor:

.. figure:: figs/Tensor.*
   :scale: 70%
   :align: center

   Output of Sample Code

      
     


