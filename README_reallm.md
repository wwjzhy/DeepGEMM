# cyberport+deepgemm

1. 安装conda环境
   
    ```bash
    enroot create --name vllm-container /home/projects/polyullm/container/qwen-nsa+0324.sqsh
    
    #激活conda环境，base
    source /root/miniconda3/etc/profile.d/conda.sh
    conda activate
    ```
    
2. conda环境中补充cuda-python
   
    ```bash
    /lustre/projects/polyullm/wenjun/cuda.tar
    ```
    
3. deepgemm安装
   
    ```bash
    git clone --recursive git@github.com:deepseek-ai/DeepGEMM.git
    
    tar -cvf 目标文件.tar 源文件夹
    
    #迁移到cyberport上，激活conda环境后，执行下面两个命令
    
    tar -xvf 压缩文件.tar 目标目录
    
    cd DeepGEMM
    
    #建立cute和cutlass软连接
    python setup.py develop
    
    python tests/test_jit.py
    
    python tests/test_core.py
    ```
    
4. check
   
    ```bash
    #保证下面软连接指向DeepGEMM路径
    vim /root/miniconda3/lib/python3.10/site-packages/deep-gemm.egg-link
    
    #如果不是,执行以下命令
    rm /root/miniconda3/lib/python3.10/site-packages/deep-gemm.egg-link
    ln -s 新路径 /root/miniconda3/lib/python3.10/site-packages/deep-gemm.egg-link
    ```