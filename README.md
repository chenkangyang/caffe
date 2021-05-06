# Caffe

[![Build Status](https://travis-ci.org/BVLC/caffe.svg?branch=master)](https://travis-ci.org/BVLC/caffe)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](LICENSE)

Caffe is a deep learning framework made with expression, speed, and modularity in mind.
It is developed by Berkeley AI Research ([BAIR](http://bair.berkeley.edu))/The Berkeley Vision and Learning Center (BVLC) and community contributors.

Check out the [project site](http://caffe.berkeleyvision.org) for all the details like

- [DIY Deep Learning for Vision with Caffe](https://docs.google.com/presentation/d/1UeKXVgRvvxg9OUdh_UiC5G71UMscNPlvArsWER41PsU/edit#slide=id.p)
- [Tutorial Documentation](http://caffe.berkeleyvision.org/tutorial/)
- [BAIR reference models](http://caffe.berkeleyvision.org/model_zoo.html) and the [community model zoo](https://github.com/BVLC/caffe/wiki/Model-Zoo)
- [Installation instructions](http://caffe.berkeleyvision.org/installation.html)

and step-by-step examples.

## Custom distributions

 - [Intel Caffe](https://github.com/BVLC/caffe/tree/intel) (Optimized for CPU and support for multi-node), in particular Intel® Xeon processors.
- [OpenCL Caffe](https://github.com/BVLC/caffe/tree/opencl) e.g. for AMD or Intel devices.
- [Windows Caffe](https://github.com/BVLC/caffe/tree/windows)

## Community

[![Join the chat at https://gitter.im/BVLC/caffe](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/BVLC/caffe?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Please join the [caffe-users group](https://groups.google.com/forum/#!forum/caffe-users) or [gitter chat](https://gitter.im/BVLC/caffe) to ask questions and talk about methods and models.
Framework development discussions and thorough bug reports are collected on [Issues](https://github.com/BVLC/caffe/issues).

Happy brewing!

## License and Citation

Caffe is released under the [BSD 2-Clause license](https://github.com/BVLC/caffe/blob/master/LICENSE).
The BAIR/BVLC reference models are released for unrestricted use.

Please cite Caffe in your publications if it helps your research:

    @article{jia2014caffe,
      Author = {Jia, Yangqing and Shelhamer, Evan and Donahue, Jeff and Karayev, Sergey and Long, Jonathan and Girshick, Ross and Guadarrama, Sergio and Darrell, Trevor},
      Journal = {arXiv preprint arXiv:1408.5093},
      Title = {Caffe: Convolutional Architecture for Fast Feature Embedding},
      Year = {2014}
    }
---
# 快速安装指南
系统 Centos7
[踩坑记录](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/%E8%B8%A9%E5%9D%91.md)
基于源码master`9b89154`的改动: 
1. 支持`opencv-4.3`, [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzopencv.sh); [.zshrc](https://github.com/chenkangyang/setup/blob/181/.zshrc)
2. 支持`cuda-11.1`, `cudnn-8`
3. 支持`python38`, `boost_python38`, `numpy-1.19.4` `protobuf-3.6.0`
4. 支持`gcc-9.1.0`, [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzgcc.sh)
4. 支持`cmake-3.20.1`, [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzcmake.sh)

## 安装C++依赖
新建一个`conda`环境，python==3.8；
或者老环境里一定要删除`protobuf`

```shell
conda uninstall protobuf
conda uninstall libprotobuf
pip uninstall protobuf
which protobuf
```

```shell
conda install -c conda-forge glog
conda install -c conda-forge zlib
conda install -c conda-forge openblas
conda install -c conda-forge lmdb
conda install -c conda-forge leveldb
conda install -c conda-forge boost
conda install -c conda-forge hdf5
```
版本对照表
```shell
    # packages in environment at /home/zhangwenting/anaconda3/envs/beta:
    #
    # Name                    Version                   Build  Channel
    glog                      0.4.0                h49b9bf7_3    conda-forge
    zlib                      1.2.11            h516909a_1010    conda-forge
    openblas                  0.3.12          pthreads_h43bd3aa_1    conda-forge
    lmdb                      0.9.24               h516909a_0    conda-forge
    leveldb                   1.22                 h7cfaab3_1    conda-forge
    boost                     1.74.0           py38hf6732f7_2    conda-forge
    hdf5                      1.12.0          nompi_h54c07f9_102    conda-forge
```

`gcc-9.1.0` [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzgcc.sh)
`cmake-3.20.1` [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzcmake.sh)
`opencv-4.3` [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzopencv.sh)
`protobuf-3.6.0` [源码](https://github.com/protocolbuffers/protobuf/releases/download/v3.6.0/protobuf-all-3.6.0.tar.gz)编译:
```shell
wget https://github.com/google/protobuf/releases/download/v3.6.0/protobuf-3.6.0.tar.gz
tar -zxvf protobuf-3.6.0.tar.gz 
cd protobuf-3.6.0/ 
./configure --prefix=/your/install/path 
make 
make install
```
## 自动搜索配置
```shell
cd caffe
mkdir build
cd build
cmake ..
```
## 手动配置路径

```shell
cd build
ccmake ..
```
[完整参考](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/ccmake-5-6.log)

这一步自动生成 `build/Makefile`

## 编译
```shell
cd build
make -j"$(nproc)" 1> make-5-6.log 2> make-5-6.error 
```
[日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/make-5-6.log)

## 安装测试
```shell
cd build
make install 1> install-5-6.log 2> install-5-6.error
```
[安装日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/install-5-6.log)

---

```shell
cd build
make runtest 1> runtest-5-6.log 2> runtest-5-6.error 
```
[测试日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/runtest-5-6.log)

## 编译安装python接口
- 编译
```shell
cd build
make pycaffe 1> pycaffe-5-6.log 2> pycaffe-5-6.error 
```
[编译日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/pycaffe-5-6.log)

---

- 安装
```shell
cd build
make pycaffe install
-- Up-to-date: /home/zhangwenting/software/caffe/build/install/python/caffe/_caffe.so

```
检查pycaffe的`_caffe.so`对应依赖是否完整
```shell
ldd $HOME/software/caffe/build/install/python/caffe/_caffe.so > ldd_caffe.so.log
```
[依赖路径](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/ldd_caffe.so-5-6.log)

---
- 版本发布
caffe的python接口也依赖于C代码，所以发布的pycaffe版本里头文件库文件都包含
```shell
cp -r ~/software/caffe/build/install ~/software/caffe-1.0.0-linux-x86_64
cp -r ~/software/caffe/build/install/python ~/software/pycaffe-1.0.0
```
- **pycaffe依赖安装**
```shell
cd ~/software/pycaffe-1.0.0
pip install -r requirements.txt
ll ~/software/pycaffe-1.0.0
```
python中引入caffe模块

- 途径一：环境变量中加入
```shell
export PYTHONPATH=~/software/pycaffe-1.0.0:$PYTHONPATH
python -c "import caffe"
```
- 途径二：每次导入caffe包的时候，加入搜索路径
```shell
import sys
sys.path.insert(0, "/home/zhangwenting/software/caffe-1.0.0-linux-x86_64/python")
import caffe
```
- 途径三：`caffe`包放入`lib/python3.8/site-packages`
```
cd site-packages
ln -s ~/software/pycaffe-cu11-1.0.0/caffe .
python -c "import caffe"
```

# Release

For all: [caffe-1.0.0-linux-x86_64](https://github.com/chenkangyang/caffe/releases/download/v1.0/caffe-1.0.0-linux-x86_64.tar.gz)
For python: [pycaffe-1.0.0](https://github.com/chenkangyang/caffe/releases/download/v1.0/pycaffe-1.0.0.tar.gz)
 
- [x] Support: `CentOS Linux release 7.2.1511` `CUDA-11.1` `CuDNN-8`
- [x] Support: `gcc 9.1.0` `c++11` `cmake 3.20.1`
- [x] Support: `opencv-4.3`
- [x] Support: `python3.7` `numpy 1.19.2` `protobuf-3.6` 

# pycaffe环境移植指南

## C++依赖
`lld pycaffe-1.0.0/_caffe.so` 看缺少哪些动态库，就安装哪些动态库

`conda install -c confa-forge 库名称` 如果有 sudo 权限就 `yum install` `apt-get`
找不到的就自己编译一下，包管理工具的好处：解决了依赖之间的版本对应关系，避免踩坑

```
conda install -c conda-forge glog=0.4.0 
conda install -c conda-forge lmdb=0.9.24
conda install -c conda-forge openblas
conda install -c conda-forge leveldb=1.18
conda install -c conda-forge boost=1.74
conda install -c conda-forge hdf5=1.12
```

并且，将这些库添加到`$LD_LIBRARY_PATH`
再动态装载：`lld pycaffe-1.0.0/_caffe.so`


如果依赖是安装于`conda`的虚拟环境下的，激活`python`虚拟环境时，执行默认的`sh conda.sh`仅更新`$PATH`，不更新`$LD_LIBRARY_PATH`，而将虚拟环境下的动态库路径写入`rc`的`$LD_LIBRARY_PATH`，非常不优雅。**所以，需要修改`conda.sh`脚本，改成动态更新`$LD_LIBRARY_PATH`(激活虚拟环境时，更新`$LD_LIBRARY_PATH`，退出虚拟环境时，恢复`$LD_LIBRARY_PATH`)**

## python依赖

```shell
conda create -n caffe python==3.7
source activate caffe
# Download source and tar -xzvf
wget -c https://github.com/chenkangyang/caffe/releases/download/v1.0/pycaffe-1.0.0.tar.gz 
tar -zxvf pycaffe-1.0.0.tar.gz
cd pycaffe-1.0.0
pip install -r requirements
cd /your/path/to/site-packages
ln -s pycaffe-1.0.0/caffe .
python -c "import caffe"
```

# 最省事的一键安装(机器软硬件版本较新的话不推荐)

直接安装`conda` 的 `intel`镜像里最新的[caffe-1.1.6-py36_intel_1](https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/intel/linux-64/caffe-1.1.6-py36_intel_1.tar.bz2)包 (2019-09-06 02:26)

```
conda create -n caffe python==3.6
source activate caffe
conda install -c intel caffe
```