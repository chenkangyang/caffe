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
3. 支持`python37`, `boost_python37`, `numpy-1.19.2` `protobuf-3.6.0`
4. 支持`gcc-9.1.0`, [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzgcc.sh)
4. 支持`cmake-3.20.1`, [安装脚本](https://github.com/chenkangyang/setup/blob/181/zzcmake.sh)

## 安装C++依赖
新建一个`conda`环境，python==3.7；
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
    package                    |            build
    ---------------------------|-----------------
    ca-certificates-2020.12.5  |       ha878542_0         137 KB  conda-forge
    certifi-2020.12.5          |   py37h89c1867_1         143 KB  conda-forge
    gflags-2.2.2               |    he1b5a44_1004         114 KB  conda-forge
    glog-0.4.0                 |       h49b9bf7_3         104 KB  conda-forge
    openssl-1.1.1h             |       h516909a_0         2.1 MB  conda-forge
    python_abi-3.7             |          1_cp37m           4 KB  conda-forge
    zlib-1.2.11                |    h516909a_1010         106 KB  conda-forge
    libgfortran-ng-7.5.0       |      h14aa051_19          22 KB  conda-forge
    libgfortran4-7.5.0         |      h14aa051_19         1.3 MB  conda-forge
    libopenblas-0.3.12         |pthreads_hb3c22a3_1         8.2 MB  conda-forge
    openblas-0.3.12            |pthreads_h43bd3aa_1         8.7 MB  conda-forge
    lmdb-0.9.24                |       h516909a_0         660 KB  conda-forge
    leveldb-1.22               |       h7cfaab3_1         197 KB  conda-forge
    snappy-1.1.8               |       he1b5a44_3          32 KB  conda-forge
    protobuf-3.13.0            |   py37h3340039_0         696 KB  conda-forge  
    boost-1.74.0               |   py37he5a615d_2         335 KB  conda-forge
    boost-cpp-1.74.0           |       h9d3c048_1        16.3 MB  conda-forge
    bzip2-1.0.8                |       h516909a_3         398 KB  conda-forge
    icu-68.1                   |       h58526e2_0        13.0 MB  conda-forge
    hdf5-1.12.0                |nompi_h54c07f9_102         3.3 MB  conda-forge
    krb5-1.17.2                |       h926e7f8_0         1.4 MB  conda-forge
    libcurl-7.71.1             |       hcdd3856_3         302 KB  conda-forge
    libssh2-1.9.0              |       hab1572f_5         225 KB  conda-forge
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
[完整参考](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/ccmake-4-23.log)

这一步自动生成 `build/Makefile`

## 编译
```shell
cd build
make -j"$(nproc)" 1> make-4-23.log 2> make-4-23.error 
```
[日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/make-4-23.log)

## 安装测试
```shell
cd build
make install 1> install-4-23.log 2> install-4-23.error
```
[安装日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/install-4-23.log)

---

```shell
cd build
make runtest 1> runtest-4-23.log 2> runtest-4-23.error 
```
[测试日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/runtest-4-23.log)

## 编译安装python接口
- 编译
```shell
cd build
make pycaffe 1> pycaffe-4-23.log 2> pycaffe-4-23.error 
```
[编译日志](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/pycaffe-4-23.log)

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
[依赖路径](https://github.com/chenkangyang/caffe/blob/opencv4/build_logs/ldd_caffe.so-4-23.log)

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
- 途径三：`caffe`包放入`lib/python3.7/site-packages`
```
cd site-packages
ln -s ~/software/pycaffe-1.0.0/caffe .
python -c "import caffe"
```

# Release

For all: [caffe-1.0.0-linux-x86_64](https://github.com/chenkangyang/caffe/releases/download/v1.0/caffe-1.0.0-linux-x86_64.tar.gz)
For python: [pycaffe-1.0.0](https://github.com/chenkangyang/caffe/releases/download/v1.0/pycaffe-1.0.0.tar.gz)
 
- [x] Support: `CentOS Linux release 7.2.1511` `CUDA-11.1` `CuDNN-8`
- [x] Support: `gcc 9.1.0` `c++11` `cmake 3.20.1`
- [x] Support: `opencv-4.3`
- [x] Support: `python3.7` `numpy 1.19.2` `protobuf-3.6` 

python 安装 caffe 模块:

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