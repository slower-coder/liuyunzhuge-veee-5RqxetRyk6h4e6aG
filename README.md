
# Conda 使用指南


Conda 是一个开源包管理和环境管理系统，能够以跨平台的方式进行软件包的安装、管理和依赖管理，特别适用于 Python 和 R 语言的环境管理。本文整理了常见 Conda 命令的使用方法。


## 1\. 安装 Miniconda


首先，下载 Miniconda 的安装脚本并执行安装。以 Linux AArch64 架构为例：



```
./Miniconda3-latest-Linux-aarch64.sh

```

按照提示完成安装，安装完成后，`conda` 将自动可用。


## 2\. 创建并激活 Conda 环境


### 创建 Conda 环境


使用 Conda 创建一个新的虚拟环境并指定 Python 的版本（以 Python 3\.8 为例）：



```
conda create -n machine_learning_env python=3.8

```

* `-n` 参数指定环境名称，这里环境名称为 `machine_learning_env`。
* `python=3.8` 指定 Python 版本为 3\.8。


### 激活 Conda 环境


创建好环境后，使用以下命令激活它：



```
conda activate machine_learning_env

```

环境激活后，命令行提示符会变成 `(machine_learning_env)`，表示当前使用的是该环境。


### 安装环境所需依赖


通常我们会有一个 `requirements.txt` 文件列出了所有需要安装的 Python 包。使用 `pip` 来安装这些依赖包：



```
pip install -r requirements.txt

```

这个命令会自动从 `requirements.txt` 中读取并安装所有指定的包。


### 移除 Conda 环境


如果想要删除某个环境（如 `machine_learning_env`），使用以下命令：



```
conda env remove -n machine_learning_env

```

## 3\. 管理 Conda 配置


### 显示 Conda 配置的源（Channels）


Conda 使用源（Channels）来查找并下载软件包。可以使用以下命令查看当前配置的源：



```
conda config --show channels

```

### 显示 Conda 配置文件的来源


查看当前 Conda 配置文件的来源路径：



```
conda config --show-sources

```

### 修改 Conda 配置


#### 移除特定的源


如果需要删除某个源，使用以下命令：



```
conda config --remove channels 

```

#### 设置 Conda 显示源 URL


为了方便查看安装时使用的源地址，可以配置 Conda 显示源 URL：



```
conda config --set show_channel_urls yes

```

## 4\. 安装依赖库


### 安装单个软件包


使用 Conda 安装 `libffi` 软件包：



```
conda install libffi

```

### 安装 Conda\-Pack


`conda-pack` 是一个打包 Conda 环境的工具，用于将环境打包为一个压缩文件，方便迁移或分发。


#### 安装 `conda-pack`


使用 `conda-forge` 源安装 `conda-pack`：



```
conda install -c conda-forge conda-pack

```

#### 打包 Conda 环境


打包指定的环境（以 `machine_learning_env` 为例）：



```
conda pack -n machine_learning_env -o machine_learning_env.tar.gz

```

* `-n machine_learning_env` 指定要打包的环境名称。
* `-o machine_learning_env.tar.gz` 指定输出的压缩文件名。


## 5\. 其他 Conda 常用命令


### 取消激活当前环境


如果不再需要使用当前环境，可以使用以下命令取消激活：



```
conda deactivate

```

 本博客参考[豆荚加速器](https://baitenghuo.com) 。转载请注明出处！
