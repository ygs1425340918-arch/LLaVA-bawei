模仿项目的代码,练习使用,原文资料:https://towardsdatascience.com/create-your-vision-chat-assistant-with-llava-610b02c3283e

初始化autodl:
conda config --add envs_dirs /root/autodl-tmp/conda-envs   # 修改conda环境的保存路径
conda config --add pkgs_dirs /root/autodl-tmp/conda-pkgs  # 修改缓存的保村路径

conda init bash 进入初始环境
source ~/.bashrc 重启,使一条生效

创建环境:
conda create -n llava_env python=3.10 -y    # 创建新环境
conda activate llava_env   # 激活环境

下载的jupyter文件第一行,下载环境
安装环境所需库:
pip install git+https://github.com/haotian-liu/LLaVA.git@786aa6a19ea10edc6f574ad2e16276974e9aaa3a

安装完之后,numpy版本过高,需要降级
pip uninstall numpy -y    # 卸载当前numpy
pip install numpy==1.24.4   # 安装兼容版本
pip install ipywidgets   # 这个不安装也可以,美化进度条的,不安装会警告,但不报错


在导包的开头,添加环境变量,需要去hugging face下载模型

import os
# 设置 Hugging Face 镜像源
os.environ['HF_ENDPOINT'] = 'https://hf-mirror.com'

pip install ipykernel  # 使用jupyter文件的必备库
下载代码时,我选择的是jupyter文件,因为可以看到图片

创建虚拟内核(创建之前,一定要先安装ipykernel库 )

python -m ipykernel install --user --name=LLaVA --display-name "LLaVA"   
# 创建虚拟内核,用于运行jupyter
